<template>
  <main class="product-grid">
      <ProductItem v-for="product in products.items" :product="product" :key="product.ProductID" />
  </main>
</template>

<script>
import ProductItem from "./ProductItem.vue";

export default {
  name: "ProductGrid",
  props: {
    products: Object,
  },
  components: {
    ProductItem,
  },
};
</script>

<style lang="scss">
main {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
</style>
