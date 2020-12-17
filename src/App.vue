<template>
  <main id="app">
    <section class="company-info">
      <div class="company-info__title">
        <h1>{{ test_json.CompanyName }}</h1>
      </div>
      <div class="company-info__details">
        <img
          :src="
            `http://images.repzio.com/productimages/${test_json.ManufacturerID}/logo${test_json.ManufacturerID}_lg.jpg?width=200&mode=max`
          "
          :alt="test_json.CompanyName"
        />
        <div v-html="test_json.Message"></div>
      </div>
    </section>

    <ItemGrid :products="test_json.items" />
    <SalesRep :sales_rep="test_json.SalesRep" />
  </main>
</template>

<script>
import ItemGrid from "./components/Items/ItemGrid.vue";
import SalesRep from "./components/SalesRep/SalesRep.vue";
import test_json from "./data/test.json";

export default {
  name: "App",
  components: {
    ItemGrid,
    SalesRep,
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
@import url("https://fonts.googleapis.com/css2?family=Nunito+Sans:wght@300;600;900&display=swap");

html,
body {
  color: $dark;
  font-size: $font-size;
  line-height: 1.33;
  font-family: "Nunito Sans", sans-serif;

  &.overflow-hidden {
    overflow: hidden;
  }

  h1,
  h2 {
    text-transform: uppercase;
    font-weight: 900;
    letter-spacing: 0.05rem;
  }
  h1,
  h2,
  h3,
  h4 {
    color: $black;
  }
}

main {
  margin: 0 auto;
  width: 100%;
  max-width: $desktop;

  section {
    padding: 0.5rem 1rem;
    box-sizing: border-box;
  }

  .company-info {
    h1 {
      @include header-underline;
    }
    &__details {
      display: flex;
      align-items: center;
      & > * {
        margin: 0 1rem;
      }
    }
  }
}
</style>
