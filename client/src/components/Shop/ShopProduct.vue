<script setup lang="ts">

</script>

<template>
  <div class="product d-flex flex-column">
    <div class="product-image"></div>
    <div class="p-10 d-flex flex-column">
      <h4>Mocbook pro</h4>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. A quidem earum fugiat ipsam eum quod doloremque porro
      </p>
      <div class="d-flex flex-row align-items-center">
        <strong class="flex-fill">Prix: 1500€</strong>
        <button class="btn btn-primary">Ajouter au pannier</button>
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
    background: url(../../assets/macbook.jpg) center/cover;
    height: 250px;
  }
}
</style>