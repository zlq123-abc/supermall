<template>
  <div class="adult-wrap">
    <div :class="{'adult-prop' : isPropUp}"></div>
    <div class="prop-up"
      v-if="isPropUp"
      >
      <div class="prop-title">提示</div>
      <div class="prop-info">资料上传还未开始，请耐心等待</div>
      <div class="prop-btn" @click="propBtn">确定</div>
    </div>

    <div>
      <!-- 其中一个模块 -->
      <!-- 第一个模块 -->
      <div
        class="item-all"
        v-for="(item, index) in productList"
        :key="index"
      >
        <div class="item-top">
          <div class="item-left">
            <img class="school-logo" src="" alt="">
            <span class="school-name">北京印刷学院</span>
          </div>
          <!-- 审核通过状态 -->
          <!-- 未上传 -->
          <img v-if="item.ziLiaoZT  == 1 && item.shenHeZT == 1" class="approved" src="" alt="未上传">
          <img v-if="item.ziLiaoZT  == 2 && item.shenHeZT == 2" class="approved" src="" alt="审核中">
          <img v-if="item.ziLiaoZT  == 2 && item.shenHeZT == 3" class="approved" src="" alt="审核通过">
          <img v-if="item.ziLiaoZT  == 1 && item.shenHeZT == 4" class="approved" src="" alt="审核不通过">
          <img v-if="item.ziLiaoZT  == 3 && item.shenHeZT == 1" class="approved" src="" alt="未上传">
          <img v-if="item.ziLiaoZT  == 3 && item.shenHeZT == 2" class="approved" src="" alt="审核中">
          <img v-if="item.ziLiaoZT  == 3 && item.shenHeZT == 4" class="approved" src="" alt="审核不通过">
        </div>
        <div class="exam-type">
          2021年研究生招生考试
        </div>
        <div class="exam-time">
          2021年7月21日00:00:00至2021年7月21日00:00:00
        </div>
        <div class="btn-all">
          <button v-if="item.ziLiaoZT == 1" class="to-upload" @click="toUpLoad">去上传</button>
          <button v-if="item.ziLiaoZT == 2" class="to-see">查看</button>
          <button v-if="item.ziLiaoZT == 3" class="to-overdue">已过期</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Profile',
  data () {
    return {
      isPropUp: false, // 是否弹框
      productList: [
        // 1:去上传  2：查看  3：已过期
        // 1:未上传  2：审核中  3：审核通过  4：审核不通过
        {ziLiaoZT: 1, shenHeZT: 1},
        {ziLiaoZT: 2, shenHeZT: 2},
        {ziLiaoZT: 2, shenHeZT: 3},
        {ziLiaoZT: 1, shenHeZT: 4},
        {ziLiaoZT: 3, shenHeZT: 1},
        {ziLiaoZT: 3, shenHeZT: 2},
        {ziLiaoZT: 3, shenHeZT: 4}
      ]
    }
  },
  computed: {

  },
  mounted () {

  },
  methods: {
    // 去上传
    toUpLoad () {
      this.isPropUp = true
    },
    // 弹框"确定按钮"
    propBtn () {
      this.isPropUp = false
    }
  }
}
</script>

<style scoped>
.adult-wrap{
  padding: 16px 16px 16px;
  height: 100%;
  width: 100%;
}
.item-all{
  padding: 12px 12px 8px 16px;
  margin-bottom: 16px;
  box-shadow: 0px 1px 15px 0px rgba(0,0,0,0.06);
}
.item-top{
  display: flex;
  justify-content: space-between;
}
.item-left{
  display: flex;
  align-items: center;
  padding: 4px 0 8px 0;
}
.school-logo{
  width: 40px;
  height: 40px;
  background-color: green;
}
.school-name{
  margin-left: 8px;
  font-weight: 500;
  color: #333333;
}
.approved{
  width: 54px;
  height: 39px;
  background-color: hotpink;
}
.exam-type{
  font-size: 14px;
  font-weight: 400;
  color: #333333;
}
.exam-time{
  padding: 4px 0 8px 0;
  font-size: 12px;
  font-weight: 400;
  color: #606060;
}
.btn-all{
  display: flex;
  justify-content: flex-end;
}
.to-upload{
  color: #ffffff;
  font-size: 14px;
  font-weight: 500;
  width: 82px;
  height: 32px;
  border-radius: 16px;
  margin-left: 4px;
  border: none;
  background: #3b6bff;
}
.to-see{
  color: #3b6bff;
  font-size: 14px;
  font-weight: 500;
  width: 82px;
  height: 32px;
  border-radius: 16px;
  margin-left: 4px;
  border: 1px solid #3b6bff;
  background-color: #ffffff;
}
.to-overdue{
  color: #ffffff;
  font-size: 14px;
  font-weight: 500;
  width: 82px;
  height: 32px;
  border-radius: 16px;
  margin-left: 4px;
  border: 1px solid #3b6bff;
  background: #909090;
}

/* 弹框样式 */
.adult-prop{
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  opacity: 0.4;
  background: #000000;
  width: 100%;
  height: 100%;
  z-index: 500;
}
.prop-up{
  opacity: 1;
  width: 270px;
  height: 160px;
  background-color: #ffffff;
  border-radius: 12px;
  z-index: 1000;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.prop-title{
  text-align: center;
  padding:19px 0 17px 0;
  font-size: 17px;
  font-weight: 500;
  color: #333333;
}
.prop-info{
  font-size: 14px;
  font-weight: 400;
  text-align: center;
  color: #333333;
  padding-bottom: 36px;
  border-bottom: #e3e4e5 solid 1px;
}
.prop-btn{
  padding: 16px 0 10px;
  text-align: center;
  font-weight: 500;
  color: #3b6bff;
}
</style>
