<template>
  <div class="footer-section">
    <van-button type="primary" @click="$emit('on-add')">加入购物车</van-button>
    <van-button type="info" @click="$emit('on-buy')">立即购买</van-button>
  </div>
</template>

<script>
export default {}
</script>

<style lang="less" scoped>
.footer-section {
  display: flex;
  > button {
    width: 100%;
  }
}
</style>
