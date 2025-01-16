<script setup lang="ts">
defineProps({
  product: Object,
});

const emit = defineEmits(["deleteProductFromCart"]);
</script>

<template>
  <div class="mb-10 p-10 d-flex flex-row align-items-center product">
    <strong class="flex-fill mr-10">{{ product.title }}</strong>
    <span class="mr-10">{{ product.price }}€</span>
    <button
      @click="emit('deleteProductFromCart', product.id)"
      class="btn btn-danger"
    >
      Delete
    </button>
  </div>
</template>

<style lang="scss" scoped>
.product {
  border: var(--border);
  border-radius: var(--border-radius);
  background-color: var(--gray-1);
}
</style>
