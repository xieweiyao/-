<template>
    <div id="tmp1">
        <div class="title">
            <h4 v-text="info.title"></h4>
            <p>{{info.add_time | datefmt('YYYY-MM-DD HH-mm-ss')}} {{info.click}}点击数</p>
        </div>
        <div id="content" v-html="info.content">
        </div>
    </div>
</template>
<script>
import {Toast} from 'mint-ui';
import common from '../../kits/common.js';
export default{
    data(){
        return {
            id:0,
            info:{}
        }
    },
    created(){
     this.id=this.$route.params.id;
     this.getnewsinfo();
    },
    methods:{
        
        getnewsinfo(){
            var url=common.apidomain+'/api/getnew/'+this.id;
           this.$http.get(url).then(function(res){
               if(res.body.status!=0){
                   Toast(res.body.message);
               }
               this.info=res.body.message[0];
           })
        }

    }
}
</script>
<style scoped>
.title h4 {
    color: #0094ff;
    /*color:red;*/
}

.title p {
    color: rgba(0, 0, 0, 0.5);
}

.title,
#content {
    padding: 5px;
}
</style>