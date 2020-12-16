<template>
  <div id="app">
  <button @click="$refs.modalName.openModal()">Open modal</button>
    <ProductGrid :products="test_json" />
    
    <modal ref="modalName">
      <template v-slot:header>
        <h1>product title</h1>
      </template>

      <template v-slot:product>
        product info
      </template>
      <template v-slot:company>
        company info
      </template>

      <template v-slot:footer>
        <div>
          <button @click="$refs.modalName.closeModal()">close</button>
        </div>
      </template>
    </modal>
  </div>
</template>

<script>
import ProductGrid from "./components/ProductGrid.vue";
import Modal from "./components/Modal.vue";
import test_json from "./data/test.json";

export default {
  name: "App",
  components: {
    ProductGrid,
    Modal
  },
  data() {
    return {
      test_json,
    };
  },
};
</script>

<style lang="scss">
@import "scss/main";

#app {
  margin: 0 auto;
  width: 100%;
  max-width: $desktop;
  
  &.overflow-hidden {
    overflow: hidden;
  }
}
</style>
