<template>
  <div class="good-card-section">
    <div class="card" v-for="(item, i) in row" :key="i">
      <van-image class="card-img" width="70" height="70" :src="item.img" />
      <div class="card-flex">
        <div class="title">{{item.title}}</div>
        <div class="total">
          <span class="total-price">￥{{item.price}}</span>
          <van-stepper class="total-num" v-model="item.num" @change="calcPrice($event, item)"/>
        </div>
      </div>
    <div>总价：{{setValue(item)}}</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    row: {
      type: Array,
      default: () => []
    }
  },
  data() {
    return {
    }
  },
  computed: {
    setValue() {
      return (item) => {
        return item.price * (item.num || 1)
      }
    }
  },
  methods: {
      calcPrice(val, item) {
        this.value = val*item.price
      }
  },
};
</script>

<style lang="less">
.good-card-section {
  .card {
    display: flex;
    padding: 10px;
    .card-flex {
      flex: 1;
      margin-left: 20px;
      line-height: 33px;
      .title {
      }
      .total {
        display: flex;
        .total-price {
        }
        .total-num {
          flex: 1;
          text-align: center;
        }
      }
    }
  }
}
</style>