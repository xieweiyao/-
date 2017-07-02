<template>
    <div id='tmpl'>
        <!--1.0 利用mint-ui的mt-swipe组件实现轮播图-->
       
        <!--2.0 利用MUI的九宫格组件实现实现导航区域-->
    </div>
</template>

<script>
// 使用 mint-ui 中的 Toast组件实现弹窗效果

</script>

<style scoped>
.mint-swipe {
    height: 300px;
}

.mint-swipe-item {
    background-color: red;
    width: 100%;
    height: 300px;
}

.mint-swipe-item img {
    width: 100%;
    height: 300px;
    display: block;
}

.mui-content,
.mui-content ul {
    background-color: #fff;
}

.mui-grid-view.mui-grid-9 .mui-table-view-cell {
    border-right: 0px;
    border-bottom: 0px;
}

.mui-grid-view.mui-grid-9 {
    border-top: 0px;
    border-left: 0px;
}

.mui-icon-home:before,
.mui-icon-email:before,
.mui-icon-chatbubble:before,
.mui-icon-location:before,
.mui-icon-search:before,
.mui-icon-phone:before {
    content: '';
    display: inline-block;
    width: 50px;
    height: 50px;
    background-repeat: round;
}

.mui-icon-home:before {
    background-image: url(../../statics/imgs/1.png);
}

.mui-icon-email:before {
    background-image: url(../../statics/imgs/2.png);
}

.mui-icon-chatbubble:before {
    background-image: url(../../statics/imgs/3.png);
}

.mui-icon-location:before {
    background-image: url(../../statics/imgs/4.png);
}

.mui-icon-search:before {
    background-image: url(../../statics/imgs/5.png);
}

.mui-icon-phone:before {
    background-image: url(../../statics/imgs/6.png);
}
</style>