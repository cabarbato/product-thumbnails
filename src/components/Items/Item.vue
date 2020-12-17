<template>
  <div class="item-info">
    <div class="item-info__image">
      <img
        :src="`${product.PhotoName}?width=750&mode=max`"
        :alt="product.ItemName"
      />
    </div>
    <div class="item-info__text">
      <div class="item-info__text-title">
        <h3>{{ product.ItemName }}</h3>
      </div>
      <div class="item-info__text-price">
        <hr />
        <h4>${{ product.BasePrice.toFixed(2) }}</h4>
        <button>see details</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Item",
  props: {
    product: Object,
  },
};
</script>

<style scoped lang="scss">
@import "../../scss/main";
.item-info {
  position: relative;
  min-height: calc(250px - 1rem);
  cursor: pointer;
  box-sizing: border-box;
  border: 1px solid $light;
  border-radius: 2px;
  box-shadow: 0px 1px 4px rgba(0, 0, 0, 0.07);
  transition: 300ms;
  overflow: hidden;
  display: inline-flex;
  align-items: center;

  &:hover {
    box-shadow: 0px 1px 5px rgba(0, 0, 0, 0.2);
    img {
      filter: grayscale(1) blur(0.6rem);
    }
    & > div {
      opacity: 1;
    }
  }

  &__image {
    z-index: -1;
    img {
      transition: 300ms;
      max-width: 100%;
      max-height: 100%;
    }
  }

  &__text {
    //opacity: 0;
    z-index: 1;
    top: 0.5rem;
    left: 0.5rem;
    transform: translate(50%, -50%, 0%);
    position: absolute;
    transition: 300ms;
    text-align: center;
    width: calc(100% - 1rem);
    height: calc(100% - 1rem);
    box-sizing: border-box;
    padding: 1rem;
    background: rgba(0, 0, 0, 0.33);
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;

    &-title {
      flex-grow: 2;
      display: flex;
      align-items: center;

      h3 {
        text-transform: uppercase;
        color: $white;
      }
    }

    &-price {
      width: 100%;

      h4 {
        color: $white;
        margin: 1rem auto;
      }

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
        padding: 0.67rem 1.5rem;
        margin: 0 auto 1rem;
        pointer-events: none;
      }
    }
  }
}
</style>
