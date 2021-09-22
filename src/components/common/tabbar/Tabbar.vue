<template>
    <ul class="tab-bar">
        <router-link tag="li" to="/home">
            <span class="iconfont icon-shouye"></span>
            <span class="title">首页</span>
        </router-link>
        <router-link tag="li" to="/category">
            <span class="iconfont icon-sort"></span>
            <span class="title">分类</span>
        </router-link>
        <router-link tag="li" to="/cart">
            <span class="iconfont icon-gouwuche"></span>
            <span class="title">购物车</span>
        </router-link>
        <router-link tag="li" to="/profile">
            <span class="iconfont icon-wodejuhuasuan"></span>
            <span class="title">我的</span>
        </router-link>
    </ul>
</template>

<script>
import '../../../assets/iconfont/iconfont.css'
export default {
  name: 'Tabbar'
}
</script>

<style scoped>
.tab-bar{
    display: flex;
    height: 50px;
    background-color: rgb(238, 237, 237);

    position: fixed;
    right: 0;
    bottom: 0;
    left: 0;
    box-shadow: 0 -3px 1px rgba(100,100,100,.2);
}
.tab-bar li{
    flex-grow: 1;
    text-align: center;
}
.iconfont{
    font-size: 20px;
}
.title{
    display: block;
    font-size: 18px;
}
.active{
    /* color: lightseagreen; */
    color: var(--color-high-text);
    font-weight: bold;
}
</style>
