<script setup lang="ts">
import type { ProductInterface } from "@/interfaces";

defineProps<{
  product: ProductInterface;
}>();

const emit = defineEmits<{
  (e: "addProductToCart", productId: number): void;
}>();
</script>

<template>
  <div class="product d-flex flex-column">
    <div class="product-image" :style="{ backgroundImage: `url(${product.image})` }"></div>
    <div class="p-10 d-flex flex-column">
      <h4>{{ product.title }}</h4>
      <p>
        {{ product.description }}
      </p>
      <div class="d-flex flex-row align-items-center">
        <strong class="flex-fill">Prix: {{ product.price }}€</strong>
        <button @click="emit('addProductToCart', product.id)" class="btn btn-primary">
          Ajouter au pannier
        </button>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.product {
  background: #fff;
  border: var(--border);
  border-radius: var(--border-radius);

  &-image {
    border-top-right-radius: var(--border-radius);
    border-top-left-radius: var(--border-radius);
    height: 250px;
    background-position: center;
    background-size: cover;
  }
}
</style>
