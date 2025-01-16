<script setup lang="ts">
defineProps({
  product: Object,
});
const emit = defineEmits(["addProductToCart"]);
</script>

<template>
  <div class="product d-flex flex-column">
    <div
      class="product-image"
      :style="{ backgroundImage: `url(${product.image})` }"
    ></div>
    <div class="p-10 d-flex flex-column">
      <h4>{{ product.title }}</h4>
      <p>
        {{ product.description }}
      </p>
      <div class="d-flex flex-row align-items-center">
        <strong class="flex-fill">Prix:{{ product.price }}€</strong>
        <button
          @click="emit('addProductToCart', product.id)"
          class="btn btn-primary"
        >
          Add to cart
        </button>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.product {
  background-color: #fff;
  border: var(--border-radius);
  &-image {
    border-top-left-radius: var(--border-radius);
    border-top-right-radius: var(--border-radius);
    background-image: url(../../assets/macbook.jpg);
    background-size: cover;
    background-position: center;
    height: 250px;
  }
}
</style>
