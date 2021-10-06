<template>
  <div>
    <header>
      <button v-on:click="navigateTo('products')">View products</button>
      {{ cart.length }} in cart
      <button v-on:click="navigateTo('cart')">View Cart</button>
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
      cart: [],
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
    },
  },
  components: { Products, Cart },
};
</script>

<style>
body {
  margin: 0;
  background-color: rgb(252, 110, 66);
}
.products {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  margin-left: 20px;
  justify-content: center;
}
.products button {
  padding: 10px;
  background-color: black;
  color: rgb(204, 74, 14);
  outline: none;
  border: none;
  cursor: pointer;
}
.products button:hover {
  color: peru;
}
</style>

<style scoped>
header {
  height: 100px;
  box-shadow: 2px 2px 5px rgb(223, 74, 48);
  background-color: white;
  text-align: right;
  font-size: 30px;
  padding-top: 20px;
}
header button {
  padding: 10px;
  border: none;
  cursor: pointer;
  color: white;
  background-color: brown;
  box-shadow: 2px 2px 5px rgb(223, 74, 48);
}
header button:hover {
  color: rgb(204, 90, 14);
}
</style>