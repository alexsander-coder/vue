<template>
  <div>
    <h1>Catalogo</h1>
    <div class="produtos">
      <div v-for="(product, index) in produtos" :key="index">
        <h3>{{product.name}}</h3>
        <div class="cost">{{product.cost}}</div>
        <img :src="product.image" />
        <button v-on:click="addItemToCart(product)">Adicionar</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      produtos: [
        {
          name: "Bola",
          cost: "R$0.00",
          image:
            ""
        {
          name: "Avião",
          cost: "R$5.99",
          image:
            ""
        }
      ]
    };
  },
  methods: {
    addItemToCart(product) {
      this.$emit("addItemToCart", product);
    }
  }
};
</script>
