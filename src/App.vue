<template>
  <div id="app">
    <router-view></router-view>
    <tabbar></tabbar>
  </div>
</template>

<script>
import Tabbar from './components/common/tabbar/Tabbar.vue'
export default {
  name: 'App',
  components: {
    Tabbar
  }
}
</script>

<style>
  @import './assets/css/base.css';
</style>
