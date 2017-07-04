<template>
    <div id='tmp1'>
        <ul class="mui-table-view">
				<li v-for="item in list" class="mui-table-view-cell mui-media">
					<router-link v-bind="{to:'/news/newsinfo/'+item.id}">
						<img class="mui-media-object mui-pull-left" :src="item.img_url">
						<div class="mui-media-body">
						    <h4>{{item.title}}</h4>
							<p class='mui-ellipsis'>{{item.zhaiyao}}</p>
                            <div class="ft">
                                发表时间:<span>{{item.add_time | datefmt('YYYY-MM-DD HH:mm:ss')}}</span>
                                点击数:<span class="click">{{item.click}}</span>
                            </div>
						</div>
					</router-link>
				</li>
			</ul>
    </div>
</template>

<script>
   import {Toast} from 'mint-ui';
   import common from '../../kits/common.js';
   export default{
     data(){
        return{
            list:[]
        }
     },
     created(){
       this.getnewslist();
     },
     methods:{  
         getnewslist(){
            //  this.list=[
            //      {  "id":13,
            //     "title":"1季度多家房企利润跌幅超50% 去库存促销战打响",
            //     "add_time":"2015-04-16T03:50:28.000Z",
            //     "zhaiyao":"房企一季度销售业绩已经陆续公布，克而瑞研究中心统计",
            //     "click":1,
            //     "img_url":"http://ofv795nmp.bkt.clouddn.com//upload/201504/16/201504161149414479.jpg"

            //      },
            //       {  "id":13,
            //     "title":"1季度多家房企利润跌幅超50% 去库存促销战打响",
            //     "add_time":"2015-04-16T03:50:28.000Z",
            //     "zhaiyao":"房企一季度销售业绩已经陆续公布，克而瑞研究中心统计",
            //     "click":1,
            //     "img_url":"http://ofv795nmp.bkt.clouddn.com//upload/201504/16/201504161149414479.jpg"

            //     }
            //  ]
            var url=common.apidomain+'/api/getnewslist';
            this.$http.get(url).then(function(res){
                if(res.body.status!=0){
                    Toast(res.body.message);
                    return;
                }
                this.list=res.body.message;
            })
             
     }
   }
}
</script>

<style scoped>
.mui-table-view img {
    width: 80px;
    height: 80px;
}

.mui-table-view .mui-media-object {
    max-width: 80px;
    line-height: 80px;
}

.ft {
    margin-top: 1.5em;
    font-size: 14px;
    color: #0094ff;
}

.ft .click {
    margin-left: 20px;
}
</style>
