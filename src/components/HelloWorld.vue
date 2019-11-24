<template>
  <div class="hello-world">
    <van-tabs v-model="active">
      <van-tab title="标签 1">
        <Card :row="cardList"></Card>
      </van-tab>
      <van-tab title="标签 2">内容 2</van-tab>
    </van-tabs>
    <Footer @on-add="add" @on-buy="buy"></Footer>
  </div>
</template>

<script>
import Card from "./card";
import Footer from "./footer";
export default {
  components: { Card, Footer },
  data() {
    return {
      active: 2,
      cardList: [
        {
          img: "https://img.yzcdn.cn/vant/cat.jpeg",
          title: "猫",
          price: "200",
          num: 0
        }
      ]
    };
  },
  methods: {
    add() {
      this.dialog('加入购物车')
    },
    buy() {
      this.dialog('立即购买')
    },
    dialog(message) {
      this.$dialog
        .confirm({
          title: "确认",
          message: message
        })
        .then(() => {
          // on close
        });
    }
  }
};
</script>

<style lang="less" scoped>
.hello-world {
  display: flex;
  flex-direction: column;
  height: 100%;
  /deep/ .van-tabs {
    flex: 1;
  }
}
</style>