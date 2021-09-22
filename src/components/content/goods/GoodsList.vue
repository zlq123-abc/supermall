<template>
    <div class="goods">
        <div v-for="(item,index) in goods" :key="index">
            <div class="goods-list">
                <img :src="item.show.img" alt="">
                <p>{{item.title}}</p>
                <div class="price-collect">
                    <span class="price">{{item.price}}</span>
                    <span class="iconfont icon-wujiaoxing"></span>
                    <span class="collect">{{item.cfav}}</span>
                </div>

            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'GoodsList',
  props: {
    goods: {
      type: Array,
      default () {
        return []
      }
    }
  }
}
</script>

<style scoped>
.goods{
    column-count: 2;
    column-width: 50%;
    column-gap: 10px;
    padding: 16px;
}
.goods-list{
    width: 98%;
    margin: 0 1% 10px 1%;
    box-sizing: border-box;
    break-inside: avoid; /* 必须加上 */
    box-shadow: 0 3px 4px rgba(228, 228, 228, 0.5);
}
img{
    width: 100%;
    border-radius: 6px;
}

.price-collect{
    display: flex;
    justify-content: flex-end;
    align-items: center;
    padding: 8px 0;
}
.price{
    margin-right: 10px;
    color: var(--color-tint);
}
</style>
