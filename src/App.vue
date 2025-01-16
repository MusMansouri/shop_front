<script setup>
import TheHeader from "./components/Header.vue";
import TheFooter from "./components/Footer.vue";
import Cart from "./components/Cart/Cart.vue";
import Shop from "./components/Shop/Shop.vue";
import { onMounted, reactive } from "vue";
import data from "./data/products";

// récupération des données depuis le fichier products dans data
const products = reactive([]);
const cart = reactive([]);

async function getProduct() {
  try {
    const reponse = await fetch("http://localhost:5000/");

    let data = await reponse.json();
    products.splice(0, products.length, ...data);
  } catch (error) {
    console.log(error);
  }
}

onMounted(() => {
  getProduct();
});
// creer une fonction qui va ajouter des produits au panier
function addProductToCart(productId) {
  const newProduct = products.find((product) => product.id === productId);
  cart.push(newProduct);
}

function deleteProductFromCart(productId) {
  console.log(productId);
}
</script>

<template>
  <div class="app-container">
    <TheHeader class="header" />
    <!-- passage du tableau de produit -->
    <Shop
      :productList="products"
      class="shop"
      @addProductToCart="addProductToCart"
    />
    <Cart
      :cartList="cart"
      class="cart"
      @deleteProductFromCart="deleteProductFromCart"
    />
    <TheFooter class="footer" />
  </div>
</template>

<style lang="scss">
@use "./assets/base.scss" as *;
@use "./assets/debug.scss" as *;

.app-container {
  min-height: 100vh;
  display: grid;
  grid-template-areas: "header header" "shop cart" " footer footer";
  grid-template-columns: 75% 25%;
  grid-template-rows: 48px auto 48px;
}

.header {
  grid-area: header;
}

.shop {
  grid-area: shop;
}

.cart {
  grid-area: cart;
  border-left: var(--border);
  background-color: #fff;
}

.footer {
  grid-area: footer;
}
</style>
