<template>
  <div class="wrapper" ref="wrapper">
    <ul class="content">
      <button @click="onClick">按钮</button>
      <li>分类列表1</li>
      <li>分类列表2</li>
      <li>分类列表3</li>
      <li>分类列表4</li>
      <li>分类列表5</li>
      <li>分类列表6</li>
      <li>分类列表7</li>
      <li>分类列表8</li>
      <li>分类列表9</li>
      <li>分类列表10</li>
      <li>分类列表11</li>
      <li>分类列表12</li>
      <li>分类列表13</li>
      <li>分类列表14</li>
      <li>分类列表15</li>
      <li>分类列表16</li>
      <li>分类列表17</li>
      <li>分类列表18</li>
      <li>分类列表19</li>
      <li>分类列表20</li>
      <li>分类列表21</li>
      <li>分类列表22</li>
      <li>分类列表23</li>
      <li>分类列表24</li>
      <li>分类列表25</li>
      <li>分类列表26</li>
      <li>分类列表27</li>
      <li>分类列表28</li>
      <li>分类列表29</li>
      <li>分类列表30</li>
      <li>分类列表31</li>
      <li>分类列表32</li>
      <li>分类列表33</li>
      <li>分类列表34</li>
      <li>分类列表35</li>
      <li>分类列表36</li>
      <li>分类列表37</li>
      <li>分类列表38</li>
      <li>分类列表39</li>
      <li>分类列表40</li>
      <li>分类列表41</li>
      <li>分类列表42</li>
      <li>分类列表43</li>
      <li>分类列表44</li>
      <li>分类列表45</li>
      <li>分类列表46</li>
      <li>分类列表47</li>
      <li>分类列表48</li>
      <li>分类列表49</li>
      <li>分类列表50</li>
      <li>分类列表51</li>
      <li>分类列表52</li>
      <li>分类列表53</li>
      <li>分类列表54</li>
      <li>分类列表55</li>
      <li>分类列表56</li>
      <li>分类列表57</li>
      <li>分类列表58</li>
      <li>分类列表59</li>
      <li>分类列表60</li>
      <li>分类列表61</li>
      <li>分类列表62</li>
      <li>分类列表63</li>
      <li>分类列表64</li>
      <li>分类列表65</li>
      <li>分类列表66</li>
      <li>分类列表67</li>
      <li>分类列表68</li>
      <li>分类列表69</li>
      <li>分类列表70</li>
      <li>分类列表71</li>
      <li>分类列表72</li>
      <li>分类列表73</li>
      <li>分类列表74</li>
      <li>分类列表75</li>
      <li>分类列表76</li>
      <li>分类列表77</li>
      <li>分类列表78</li>
      <li>分类列表79</li>
      <li>分类列表80</li>
      <li>分类列表81</li>
      <li>分类列表82</li>
      <li>分类列表83</li>
      <li>分类列表84</li>
      <li>分类列表85</li>
      <li>分类列表86</li>
      <li>分类列表87</li>
      <li>分类列表88</li>
      <li>分类列表89</li>
      <li>分类列表90</li>
      <li>分类列表91</li>
      <li>分类列表92</li>
      <li>分类列表93</li>
      <li>分类列表94</li>
      <li>分类列表95</li>
      <li>分类列表96</li>
      <li>分类列表97</li>
      <li>分类列表98</li>
      <li>分类列表99</li>
      <li>分类列表100</li>
    </ul>
  </div>
</template>

<script>
// 1.下载 npm install better-scroll --save
// 2. 引用
import BScroll from 'better-scroll'
export default {
  name: 'Category',
  data () {
    return {
      bscroll: null
    }
  },
  mounted () {
    // new BScroll()中   参数1：挂载el(在mounted()中执行)  参数2：{}对象  里面可以写多个属性

    // 属性1：probeType   实时监听滚动位置     配合 .on()事件使用
    // 默认情况下BScroll是不可以实时的监听滚动位置的，必须加一个probeType参数
    // probe  侦测
    // 0, 1 都是不侦测实时的位置
    // 2 在手指滚动的过程中侦测，手指离开后的惯性滚动过程中不侦测
    // 3 只要是滚动都侦测

    // 属性2：pullUpLoad  上拉加载更多（true）    配合 .on()事件使用   以及 this.bscroll.finishPullUp()

    this.bscroll = new BScroll(this.$refs.wrapper, {
      probeType: 3,
      pullUpLoad: true
    })

    // 监听滚动位置事件
    // 参数1：监听事件的类型   参数2：函数
    this.bscroll.on('scroll', (position) => {
      // console.log(position)
    })

    // 监听上拉加载事件
    this.bscroll.on('pullingUp', () => {
      console.log('上拉加载更多！')

      // 发送网络请求，请求更多页的数据

      // 等数据请求完成，并且将新的数据展示出来后调用 this.bscroll.finishPullUp() 进行下一次的上拉加载更多事件
      setTimeout(() => {
        this.bscroll.finishPullUp()
      }, 2000)
    })
  },

  methods: {
    onClick () {
      console.log('-------====')
    }
  }
}
</script>

<style scoped>
.wrapper {
  height: 200px;  /* 必须要有一个固定的高度 */
  overflow: hidden;
  background-color: skyblue;

}
</style>
