<template>
  <div class="hello-world">
    <van-tabs v-model="active">
      <van-tab title="商品">
        <Card :row="cardList0"></Card>
      </van-tab>
      <van-tab title="购物车">
        <Card :row="cardList1">
          <van-button type="danger" slot="btn">删除</van-button>
        </Card>
      </van-tab>
    </van-tabs>
    <Footer @on-add="add" @on-buy="buy"></Footer>
  </div>
</template>

<script>
import Card from './card'
import Footer from './footer'
export default {
  components: { Card, Footer },
  data () {
    return {
      active: 0,
      cardList1: [],
      cardList0: [
        {
          img: 'https://img.yzcdn.cn/vant/cat.jpeg',
          title: '猫',
          price: 200,
          num: 0
        },
        {
          img: 'https://img.yzcdn.cn/vant/cat.jpeg',
          title: '猫',
          price: 200,
          num: 0
        },
        {
          img: 'https://img.yzcdn.cn/vant/cat.jpeg',
          title: '猫',
          price: 200,
          num: 0
        }
      ]
    }
  },
  methods: {
    add () {
      this.dialog('加入购物车', function (_this) {
        _this.cardList1 = JSON.parse(JSON.stringify(_this.cardList0))
      })
    },
    buy () {
      this.dialog('立即购买', function (_this) {
        let count = 0
        _this[`cardList${_this.active}`].map(x => (count += x.price * x.num))
        alert('总价为：' + count)
      })
    },
    dialog (message, fn) {
      this.$dialog
        .confirm({
          title: '确认',
          message: message
        })
        .then(() => {
          // on close
          fn && fn(this)
        })
    }
  }
}
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
