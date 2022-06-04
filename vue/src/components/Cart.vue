<template>
  <div>
    <h1>Seu carrinho</h1>
    <div class="produtos">
      <div v-for="(product, index) in cart" :key="index">
        <h3>{{product.name}}</h3>
        <img :src="product.image" />
        <div>{{product.cost}}</div>
        <button v-on:click="removeItemFromCart(product)">REMOVER</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["cart"],
  methods: {
    removeItemFromCart(product) {
      this.$emit("removeItemFromCart", product);
    }
  }
};
</script>
