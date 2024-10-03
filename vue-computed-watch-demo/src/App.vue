<template>
  <div id="app">
    <h1>购物车</h1>
    <label>商品单价: <input v-model="price" type="number" /></label>
    <br>
    <label>商品数量: <input v-model="quantity" type="number" /></label>
    <br><br>

    <h3>总价 (computed): {{ totalPrice }}</h3>
    <h3>总价 (methods): {{ calculateTotalPrice() }}</h3>
    <p v-if="message">{{ message }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      price: 100,
      quantity: 1,
      message: ''
    };
  },
  computed: {
    totalPrice() {
      console.log('Computed: 重新计算总价');
      return this.price * this.quantity;
    }
  },
  watch: {
    totalPrice(newVal) {
      if (newVal > 1000) {
        this.message = '总价超过 1000 元，您可能需要重新考虑购买。';
      } else {
        this.message = '';
      }
    }
  },
  methods: {
    calculateTotalPrice() {
      console.log('Methods: 重新计算总价');
      return this.price * this.quantity;
    }
  }
};
</script>