<script setup lang="ts">
import TheHeader from "./components/Header.vue";
import TheFooter from "./components/Footer.vue";
import Cart from "./components/Cart/Cart.vue";
import Shop from "./components/Shop/Shop.vue";
import data from "./data/product";
import { reactive } from "vue";
import type { ProductInterface, ProductCartInterface } from "./interfaces";
import product from "./data/product";

const state = reactive<{
  products: ProductInterface[];
  cart: ProductCartInterface[];
}>({
  products: data,
  cart: [],
});

function addProductToCart(productId: number): void {
  const product = state.products.find((product) => product.id === productId);

  if (product) {
    const productInCart = state.cart.find(product => product.id === productId)

    if (productInCart) {
      productInCart.quantity++
    }
    else {
      state.cart.push({ ...product, quantity: 1 });
    }
  }
}

function removeProductFromCart(productId: number): void {
  const productFromCart = state.cart.find(product => product.id === productId)
  if (productFromCart) {
    if (productFromCart.quantity === 1) {
      state.cart = state.cart.filter(product => product.id !== productId)
    } else {
      productFromCart.quantity--;
    }
  }

}
</script>
<template>
  <div class="app-container">
    <TheHeader class="header" />
    <Shop :products="state.products" @add-product-to-cart="addProductToCart" class="shop" />
    <Cart :cart="state.cart" class="cart" @remove-product-from-cart="removeProductFromCart" />
    <TheFooter class="footer" />
  </div>
</template>

<style lang="scss">
@import "./assets/base.scss";
@import "./assets/debug.scss";

.app-container {
  display: grid;
  grid-template-areas: "header header" "shop cart" "footer footer";
  grid-template-columns: 75% 25%;
  grid-template-rows: 48px auto 48px;
  min-height: 100vh;
}

.header {
  grid-area: header;
}

.footer {
  grid-area: footer;
}

.shop {
  grid-area: shop;
}

.cart {
  grid-area: cart;
  border-left: var(--border);
  background: #fff;
}
</style>
