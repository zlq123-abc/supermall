<template>
    <!-- 轮播图 -->
    <van-swipe class="my-swipe" :autoplay="2000" indicator-color="white">
        <van-swipe-item v-for="(item,index) in banners" :key="index">
        <a :href="item.link">
            <img class="banner-img" :src="item.image" alt="">
        </a>
        </van-swipe-item>
    </van-swipe>
</template>

<script>
import Vue from 'vue'
import {Swipe, SwipeItem} from 'vant'
Vue.use(Swipe)
Vue.use(SwipeItem)
export default {
  name: 'HomeSwiper',
  props: {
    banners: {
      type: Array,
      // 默认值
      default () {
        return []
      }
    }
  }
}
</script>

<style scoped>
.my-swipe {
    width: 100%;
    height: 180px;
  }

.banner-img{
  width: 100%;
  height: 100%;
}
</style>
