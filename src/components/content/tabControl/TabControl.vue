<template>
    <div class="tabcontrol">
        <div
        v-for="(item,index) in titles"
        :key="index"
        class="tabcontrol-item"
        :class="{'activeItem' : index === currentIndex}"
        @click="itemClick(index)">
            <span>{{item}}</span>
        </div>
    </div>
</template>

<script>
export default {
  name: 'TabControl',
  props: { // 父传子（外部发生变化向内部传）
    titles: {
      type: Array,
      default () {
        return []
      }
    }
  },
  data () {
    return {
      currentIndex: 0
    }
  },
  methods: {
    itemClick (index) {
      this.currentIndex = index
      // 子传父（内部发生变化向外部传递）
      this.$emit('tabClick', index)
    }
  }
}
</script>

<style scoped>
.tabcontrol{
    display: flex;
    background-color: #fff;
    height: 40px;
    line-height: 40px;
    text-align: center;
}
.tabcontrol-item{
    flex-grow: 1;
}

.tabcontrol-item span{
    padding: 5px;
}

.activeItem{
    color: var(--color-tint);
}
.activeItem span{
    border-bottom: 3px solid var(--color-tint);
}
</style>
