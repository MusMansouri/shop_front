<script setup lang="ts">
import CartProductList from "./CartProductList.vue";
defineProps({
  cartList: Array,
});
</script>

<template>
  <div class="p-20">
    <h2 class="mb-10">Panier</h2>
    <CartProductList :cartlist="cartList" />
  </div>
</template>

<style lang="scss" scoped></style>
