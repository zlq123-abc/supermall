<template>
    <div class="recommend">
        <div class="img-title" v-for="(item,index) in recommends" :key="index">
            <a :href="item.link" class="a-imgtitle">
                <img :src="item.image" alt="">
                <div>{{item.title}}</div>
            </a>
        </div>
    </div>
</template>

<script>
export default {
  name: 'RecommendView',
  props: {
    recommends: {
      type: Array,
      default () {
        return []
      }
    }
  }
}
</script>

<style scoped>
.recommend{
    display: flex;
    justify-content: space-evenly;
    padding: 10px 0 20px;
    border-bottom: 8px solid #eee;
}
.img-title{
    width: 75px;
    text-align: center;
}
img{
    width: 100%;
    margin-bottom: 10px;
}
</style>
