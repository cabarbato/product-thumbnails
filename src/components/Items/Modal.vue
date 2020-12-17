<template>
  <transition name="fade">
    <div class="modal" v-if="show">
      <div class="modal__backdrop" @click="closeModal()" />

      <div class="modal__dialog">
        <div class="modal__header">
          <h1>{{ selected_product.ItemName }}</h1>
          <button type="button" class="modal__close" @click="closeModal()">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 352 512">
              <path
                fill="#cfcfcf"
                d="M242.72 256l100.07-100.07c12.28-12.28 12.28-32.19 0-44.48l-22.24-22.24c-12.28-12.28-32.19-12.28-44.48 0L176 189.28 75.93 89.21c-12.28-12.28-32.19-12.28-44.48 0L9.21 111.45c-12.28 12.28-12.28 32.19 0 44.48L109.28 256 9.21 356.07c-12.28 12.28-12.28 32.19 0 44.48l22.24 22.24c12.28 12.28 32.2 12.28 44.48 0L176 322.72l100.07 100.07c12.28 12.28 32.2 12.28 44.48 0l22.24-22.24c12.28-12.28 12.28-32.19 0-44.48L242.72 256z"
              ></path>
            </svg>
          </button>
        </div>

        <div class="modal__product">
          <div class="modal__product-image">
            <img
              :src="`${selected_product.PhotoName}?height=250&mode=max`"
              :alt="selected_product.ItemName"
            />
          </div>

          <div class="modal__product-price">
            <h2>${{ selected_product.BasePrice.toFixed(2) }}</h2>
            <div>
              <h3>Item ID</h3>
              <p>{{ selected_product.ItemID }}</p>
            </div>
            <div>
              <h3>Dimensions</h3>
              <p>{{ selected_product.Dimensions }}</p>
            </div>
          </div>
        </div>

        <div v-if="selected_product.Description.length" class="modal__details">
          <div>
            <h3>Description</h3>
            <p>{{ selected_product.Description }}</p>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: "Modal",
  data() {
    return {
      show: false,
      selected_product: {},
    };
  },
  methods: {
    closeModal() {
      this.show = false;
      this.selected_product = {};
      document.querySelector("body").classList.remove("overflow-hidden");
    },
    openModal(product) {
      this.show = true;
      this.selected_product = product;
      document.querySelector("body").classList.add("overflow-hidden");
    },
  },
};
</script>

<style scoped lang="scss">
@import "../../scss/main";

.modal {
  overflow-x: hidden;
  overflow-y: auto;
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 9;
  &__backdrop {
    background-color: rgba(0, 0, 0, 0.3);
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 1;
  }
  &__dialog {
    background-color: #ffffff;
    position: relative;
    width: calc(100vw - 3rem);
    max-width: 600px;
    margin: 3rem auto;
    display: flex;
    flex-direction: column;
    border-radius: 2px;
    border: 1px solid $light;
    z-index: 2;
    padding: 1rem 2rem;
    box-sizing: border-box;
    @media screen and (max-width: 992px) {
      width: 90%;
    }
    & > hr {
      background-color: $light;
      height: 1px;
      border: none;
      width: 100%;
    }
    h1,
    h3 {
      margin: 1rem 0;
      @include header-underline;
    }
    h2 {
      color: $green;
    }
  }
  &__close {
    width: 2rem;
    height: 2rem;
    background-color: transparent;
    outline: none;
    border: none;
    cursor: pointer;
    opacity: 0.7;
    transition: 150ms;

    &:hover {
      opacity: 1;
    }
  }
  &__header {
    margin: 0;
    display: flex;
    align-items: center;
    justify-content: space-between;
    
    h1 {
    margin-right: 1rem;
    }
  }
  &__product {
    margin: 1rem 0;
    overflow: auto;
    display: flex;
    align-items: center;
    justify-content: center;
    div {
      margin-right: 1rem;
    }
    &-image {
      flex-grow: 2;
      text-align: center;
      img {
        max-width: 100%;
        height: auto;
      }
    }
    &-price {
      flex-grow: 1;
    }
  }
  &__details {
    margin: 1rem 0;
    border-top: 1px solid $light;
  }
}
.fade-enter-active,
.fade-leave-active {
  transition: 300ms;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
