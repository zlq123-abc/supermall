<template>
    <div class="adult-wrap">
      <div class="exam-name">2021本科招生考试</div>
      <!-- 高中会考证 -->
      <div class="hschool-uniexam-item">
        <div class="hschool-uniexam-top">
          <div class="hschool-uniexam-book">高中会考证</div>
          <div class="need-up-photo">需要上传2张照片</div>
          <button class="see-uniexam-sample">查看样例</button>
        </div>
        <div class="photo-tips">上传图片要求清晰明了，不得遮挡</div>
        <div class="exam-photo-list">
          <img class="photp-list-core" src="" alt="">
          <img class="photo-list-del" src="" alt="">
        </div>
      </div>
      <!-- 高中毕业证 -->
      <div class="hschool-gradu-item">
        <div class="hschool-gradu-top">
          <div class="hschool-gradu-book">高中毕业证</div>
          <div class="need-up-photo">请上传1份PDF文件</div>
          <button class="see-gradu-sample">查看样例</button>
        </div>
        <img class="hschool-gradu-pdf" src="" alt="pdf文件">
      </div>
      <button class="up-load">上传</button>
    </div>
</template>

<script>
export default {
  name: 'Cart'
}
</script>

<style scoped>

</style>
