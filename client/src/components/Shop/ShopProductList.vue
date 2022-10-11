<script setup lang="ts">
import ShopProduct from "./ShopProduct.vue";
import type { ProductInterface } from "@/interfaces";

defineProps<{
  products: ProductInterface[];
}>();

const emit = defineEmits<{
  (e: "addProductToCart", productId: number): void;
}>();
</script>

<template>
  <div class="grid p-20">
    <ShopProduct @add-product-to-cart="emit('addProductToCart', $event)" v-for="product in products" :key="product.id"
      :product="product" />
  </div>
</template>

<style lang="scss" scoped>
.grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: 400px;
  gap: 20px;
}
</style>
