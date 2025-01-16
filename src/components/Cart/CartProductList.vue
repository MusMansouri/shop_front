<script setup lang="ts">
import CartProduct from "./CartProduct.vue";

defineProps({
  cartlist: Array,
});
</script>

<template>
  <div>
    <CartProduct :product="product" v-for="product in cartlist" />
  </div>
</template>

<style lang="scss" scoped></style>
