<script setup>
import ShopProductList from "./ShopProductList.vue";

// récupération des données transmises depuis App
// nous récupérons un tableau de produits
defineProps({
  productList: Array,
});
const emit = defineEmits(["addProductToCart"]);
</script>

<template>
  <div class="p-20">
    <ShopProductList
      :productList="productList"
      @add-product-to-cart="(productId) => emit('addProductToCart', productId)"
    />
  </div>
</template>
