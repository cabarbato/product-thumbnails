<template>
  <div
    class="grid-item"
    :style="{
      backgroundImage: `url(${product.PhotoName}?width=750&mode=max`,
    }"
  >
    <div class="grid-item__info">
      <div class="item-info__title">
        <h3>{{ product.ItemName }}</h3>
      </div>
      <div class="item-info__price">
        <hr />
        <p>
          as low as <strong>${{ product.PriceLevel9.toFixed(2) }}</strong>
        </p>
        <button>view details</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductItem",
  props: {
    product: Object,
  },
};
</script>

<style scoped lang="scss">
@import "../scss/variables";

.grid-item {
  width: calc(33.3% - 1rem);
  height: calc(33.3vw - 1rem);
  max-height: calc(400px - 1rem);
  margin: 0.5rem;
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  cursor: pointer;
  box-sizing: border-box;
  border: 2px solid $light;
  box-shadow: 0px 1px 8px rgba(0, 0, 0, 0.08);

  .grid-item__info {
    opacity: 0;
    transition: 300ms;
    text-align: center;
    width: calc(100% - 1rem);
    height: calc(100% - 1rem);
    box-sizing: border-box;
    padding: 1.5rem 1rem;
    color: $white;
    background: rgba(0, 0, 0, 0.33);
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;

    .item-info__title {
      flex-grow: 2;
      display: flex;
      align-items: center;

      h3 {
        text-transform: uppercase;
      }
    }

    .item-info__price {
      width: 100%;

      hr {
        outline: none;
        border: 1px solid $white;
      }
      button {
        color: $white;
        font-size: 1rem;
        background-color: transparent;
        outline: none;
        border: 2px solid $white;
        padding: 0.75rem 1.5rem;
        pointer-events: none;
      }
    }
  }

  &:hover {
    .grid-item__info {
      opacity: 1;
    }
  }
}
</style>
