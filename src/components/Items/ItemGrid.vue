<template>
  <section class="product-grid">
    <div
      v-for="(product, i) in products"
      class="grid-item"
      @click="$refs.ItemModal.openModal(product)"
      :key="i"
    >
      <Item :product="product" />
    </div>

    <modal ref="ItemModal"></modal>
  </section>
</template>

<script>
import Item from "./Item.vue";
import Modal from "./Modal.vue";

export default {
  name: "ItemGrid",
  props: {
    products: Array,
  },
  components: {
    Item,
    Modal,
  },
};
</script>

<style lang="scss">
@import "../../scss/main";
.product-grid {
  width: 100%;
  -webkit-column-gap: .5rem;
  -moz-column-gap: .5rem;
  column-gap: .5rem;
  -moz-column-count: 4;
  -webkit-column-count: 4;
  column-count: 4;

  @media (max-width: $desktop) {
    -moz-column-count: 3;
    -webkit-column-count: 3;
    column-count: 3;
  }
  @media (max-width: $tablet) {
    -moz-column-count: 2;
    -webkit-column-count: 2;
    column-count: 2;
  }
  @media (max-width: $mobile) {
    -moz-column-count: 1;
    -webkit-column-count: 1;
    column-count: 1;
  }

  .grid-item {
    margin: 0 0.25rem 1rem;
    display: block;
  }
}
</style>
