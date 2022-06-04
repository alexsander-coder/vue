<template>
  <div>
    <header>
      <button v-on:click="navigateTo('products')">Produtos</button>
      {{cart.length}} No carrinho
      <button v-on:click="navigateTo('cart')">Ver Carrinho</button>
    </header>

    <div v-if="page === 'cart'">
      <Cart v-on:removeItemFromCart="removeItemFromCart" :cart="cart" />
    </div>

    <div v-if="page === 'products'">
      <Products v-on:addItemToCart="addItemToCart" />
    </div>
  </div>
</template>

<script>
import Products from "./components/Products.vue";
import Cart from "./components/Cart.vue";

export default {
  name: "App",
  data: () => {
    return {
      page: "products",
      cart: []
    };
  },
  methods: {
    addItemToCart(product) {
      this.cart.push(product);
    },
    removeItemFromCart(product) {
      this.cart.splice(this.cart.indexOf(product), 1);
    },
    navigateTo(page) {
      this.page = page;
    }
  },
  components: { Products, Cart }
};
</script>

<style>
body {
  margin: 0;
}

.produtos {
  display: grid;
  grid-template-columns: 1fr 1fr;
}

.produtos button {
  padding: 10px;
  background-color: black;
  color: white;
  outline: none;
  border: none;
  cursor: pointer;
}
</style>

<style scoped>
header {
  height: 60px;
  box-shadow: 2px 2px 5px rgb(253, 82, 111);
  background-color: rgb(255, 0, 43);
  text-align: right;
  font-size: 30px;
  padding-top: 15px;
}

header button {
  padding: 10px;

  border: none;
  cursor: pointer;
  color: white;
  background-color: green;
}
</style>
