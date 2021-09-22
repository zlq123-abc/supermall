<template>
    <div class="home">
        <!-- 顶部导航栏 -->
        <nav-bar class="home-nav">
          <template v-slot:center>
            <div>购物街</div>
          </template>
        </nav-bar>

        <!-- 滚动 -->
        <!-- <scroll class="scroll-content">
        </scroll> -->

        <!-- 轮播图 -->
          <home-swiper :banners="banners"></home-swiper>
          <!-- 推荐信息 -->
          <recommend-view :recommends="recommends"></recommend-view>
          <!-- 特征商品信息 -->
          <feature-view></feature-view>
          <!-- 商品导航栏 (含子传父) -->
          <tab-control class="tab-control" :titles="titles" @tabClick = 'tttabClick'></tab-control>
          <!-- 分栏布局 -->
          <goods-list :goods="showGoods"></goods-list>
    </div>
</template>

<script>
// 引用
import NavBar from '../../components/common/navbar/NavBar.vue'
import HomeSwiper from './childComps/HomeSwiper.vue'
import RecommendView from './childComps/RecommendView.vue'
import FeatureView from './childComps/FeatureView.vue'
import TabControl from '../../components/content/tabControl/TabControl.vue'
import GoodsList from '../../components/content/goods/GoodsList.vue'
import {getHomeMultidata, getHomeGoods} from '../../network/home'
/* import Scroll from '../../components/common/scroll/Scroll.vue' */
export default {
  name: 'Home',
  // 注册
  components: {
    NavBar,
    HomeSwiper,
    RecommendView,
    FeatureView,
    TabControl,
    GoodsList
    /* Scroll */
  },
  data () {
    return {
      banners: [], // banner图
      recommends: [], // banner图下面 推荐信息的数据
      titles: ['流行', '新款', '精选'],
      // 商品列表
      goods: {
        'pop': {page: 0, list: []}, // 流行
        'new': {page: 0, list: []}, // 新款
        'sell': {page: 0, list: []} // 精选
      },

      currentType: 'pop' // 默认当前类型为pop
    }
  },

  computed: {
    showGoods () {
      return this.goods[this.currentType].list
    }
  },

  mounted () {
    // 1.请求多个数据
    this.getHomeMultidata()
    // 2.请求商品数据
    this.getHomeGoods('pop')
    this.getHomeGoods('new')
    this.getHomeGoods('sell')
  },
  methods: {

    /*
      事件监听相关的方法
    */
    // 动态获取当前的类型（pop new sell）
    tttabClick (index) {
      console.log(index)
      switch (index) {
        case 0:
          this.currentType = 'pop'
          break
        case 1:
          this.currentType = 'new'
          break
        case 2:
          this.currentType = 'sell'
          break
      }
    },

    /*
      网络请求相关的方法
    */
    // 1.请求多个数据（封装）
    getHomeMultidata () {
      getHomeMultidata().then(res => {
        console.log(res)
        const resData = res.data
        this.banners = resData.banner.list
        this.recommends = resData.recommend.list
      })
    },
    // 2.请求商品数据（封装）
    getHomeGoods (type) {
      const page = this.goods[type].page + 1
      getHomeGoods(type, page).then(res => {
        console.log(res) // 此时拿到的是第一页（page = 1）的数据(30条)
        this.goods[type].list.push(...res.data.list) // 将数组中的数据添加到另一个数组中的用法（此处是将第一页的数据添加到list[]中，然后下一步将页码+1）
        this.goods[type].page += 1 // 页码+1
      })
    }
  }
}
</script>

<style scoped>
.home{
  padding-top: 44px;
  height: 100vh;
}
.home-nav{
  background-color: var(--color-tint);
  color: aliceblue;

  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  z-index: 9;
}

/* 实现TabControl导航栏顶部吸力效果（移动端适用） */
.tab-control{
  position: sticky;
  top: 44px;
}

/* .scroll-content{
  height: calc(100% - 50px);
  overflow: hidden;
}  或者*/

.scroll-content{
  overflow: hidden;
  position: absolute;
  top: 44px;
  bottom: 50px;
  left: 0;
  right: 0;
}
</style>
