<template>
  <div id="tmp1">
    <!--1.0 图片分类-->
    <!--<div id='cate'>
        <ul v-bind="{style:'width:'+ulWidth+'px'}">
            <li  @click="getimages(0)">全部</li>
            <li v-for="(item,index) in cates" @click="getimages(item.id)" :key = 'index'>{{item.title}}</li>
        </ul>
    </div>-->
    <!--2.0 图片列表-->
    <!--<div id='imglist'>
        <ul>
            <li v-for="(item,index) in list" :key='index'>
                <router-link v-bind="{to:'/photo/photoinfo/'+item.id}">
                    <img v-lazy="item.img_url">
                    <div id="desc">
                        <h5 v-text="item.title"></h5>
                        <p v-text="item.zhaiyao"></p>
                    </div>
                </router-link>
            </li>
        </ul>
    </div>-->
    <!--获取列表数据-->
    <div id="cate">
        <ul v-bind="{style:'width:'+ulwidth+'px'}">
            <li @click="getimg(0)">主页</li>
            <li v-for="item in cates" @click="getimg(item.id)">{{item.title}}</li>
        </ul>
    </div>
    <!--获取图片列表-->
    <div id="imglist">
        <ul>
            <li v-for="item in list">
                <img v-lazy="item.img_url">
                <div id="desc">
                    <h5 v-text="item.title"></h5>
                    <p v-text="item.zhaiyao"></p>
                </div>
            </li>
        </ul>
    </div>
    
    
  </div>
</template>
<script>
// import common from '../../kits/common.js';
// import { Toast } from 'mint-ui';

// export default {
//   data () {
//     return {
//         ulWidth:320,
//         cates : [],   //用来存储图片分类数据的数组
//         list:[] //存储图片数据的数据
//     };
//   },
//   created(){
//         // 1.0 获取图片分类数据
//         this.getcates();

//         // 2.0 加载图片数据
//         var all = 0; //获取所有数据
//         this.getimages(all);
//     },
//   methods:{
//         getcates(){
//             // 1.0 确定url
//             var url = common.apidomain + '/api/getimgcategory';
//             // 2.0 调用$http的get方法获取数据
//             this.$http.get(url).then(function(res){
//                 if(res.body.status != 0){
//                     Toast(res.body.message);
//                     return;
//                 }

//                 // 3.0 实现数据的赋值操作
//                 this.cates = res.body.message;

//                 // 4.0 实现当前分类数据所在的ul的总宽度 = 分类个数 * 每个分类数据的宽度
//                 var w = 62;
//                 var count = res.body.message.length + 1;
//                 this.ulWidth = w * count ;

//             });
//         },
//         // 2.0 加载图片数据
//         getimages(cateid){
//             // 0.0 如果方法的cateid参数没有传递，则默认是0,代表获取所有图片数据
//             cateid = cateid || 0;
//                         // 1.0 确定url
//             var url = common.apidomain + '/api/getimages/'+cateid;
//             // 2.0 ajax请求数据
//             this.$http.get(url).then(function(res){
//                 var body = res.body;
//                 if(body.status != 0){
//                     Toast(res.body.message);
//                     return;
//                 }

//                 // 3.0 将数据复制给this.list
//                 this.list = body.message;
//             });
//         }
//     }
// }
import common from '../../kits/common.js';
import {Toast} from 'mint-ui';
//动态获取头部列表的数据
export default{
    data(){
        return{
            cates:[],
            ulwidth:320,
//             list:[{
//                 "id":	51,
// "title"	:"超甜美的韩国美女美图欣赏",
// "img_url":	"http://182.254.146.100:8080/upload/201504/18/thumb_201504181420529760.jpg",
// "zhaiyao":	"收集了甜素纯美女写真图1等精彩图片,同时汇集美女图片,搞笑图片,奇闻趣事,风景图片,明星写真,娱乐八卦,气质,清纯,非主流,美女,高清图片"
//             }]
            list:[]
        }
    },
    created(){
        this.getcates();
        var all=0;
        this.getimg(all);
    },
    methods:{
        // 加载图片
        getimg(cateid){
             cateid=cateid||0;
            var url=common.apido+'/api/getimages/'+cateid;
            this.$http.get(url).then(function(res){
                if(res.body.status!=0){
                    Toast(res.body.message)
                }
                this.list=res.body.message;
            })
        },
        getcates(){
            var url=common.apido+'/api/getimgcategory';
            this.$http.get(url).then(function(res){
                if(res.body.status!=0){
                    Toast(res.body.message);
                }
                this.cates=res.body.message;
                var cont=62;
                this.ulwidth=(res.body.message.length+1)*cont;
            })
        }
    }
}
</script>
<style scoped>
    /*1.0 图片分类*/
	#cate{
		width: 375px;
		max-width: 375px;
		overflow-x: auto;
	}
	#cate ul{
		margin: 0px;
        /*width:3000px;*/
		padding-left: 10px;
	}
	#cate li{
		cursor: pointer;
		list-style: none;
		display: inline-block;
		color:#0094ff;
		font-size: 14px;
		padding-left: 6px;
	}

	/*2.0 实现图片列表样式*/
	#imglist{

	}
	#imglist ul {
		padding-left: 0px;
	}
	#imglist li{
		list-style:none;
		position: relative ;
	}
	#imglist img{
		width:100%;
		height: 300px;
	}

	#desc{
		width: 100%;
		background-color: rgba(0,0,0,0.2);
		position: absolute;
		bottom: 2px;
		left: 0px;
	}

    #desc h5{
        color: #ffffff;
        font-weight: bold;
    }
    #desc p{
        color:#fff;
    }

    image[lazy=loading] {
        width: 40px;
        height: 300px;
        margin: auto;
    }
</style>