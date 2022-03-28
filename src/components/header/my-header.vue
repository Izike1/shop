<template>
  <div class="header">
    <my-container>
      <div class="header__body">
        <div class="header__logotype">
          <a class="header__logo">
            <img src="@/assets/image/header/logo.svg" alt="Logo">
          </a>
        </div>
        <div class="header__action">
          <my-button
              @click="showCart"
              class="button"
              textButton="Корзина"/>
          <transition name="fade">
          <my-cart
              v-model:show="cartVisible"
              @remove="removeCartItem"
              :cart-items="cartItems"
              />
          </transition>
        </div>
      </div>
    </my-container>

  </div>
</template>

<script>
import myCart from "@/components/header/my-cart";
export default {
  name: 'my-header',
  components: {
    myCart
  },
  props: {
    cartItems: {
      type: Array,
      default: () => [],
    },
    removeCartItem: {
      type: Function
    },
  },
  data() {
    return {
      cartVisible: false,
    }
  },
  methods: {
    showCart() {
      this.cartVisible = !this.cartVisible;
    },
  }
}
</script>

<style lang="scss">
.header{
  background-color: #474747;
  &__body{
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    height: 70px;
  }
  &__action{
    position: relative;
    display: flex;
    gap: 10px;
  }
}
.button{
  padding: 10px 15px;
  border: 1px solid #9eff00;
  border-radius: 10px 20px;
  transition: border-radius .2s linear;
  cursor: pointer;
  color: inherit;
  background: none;
}
.fade-enter-active, .fade-leave-active {
  transition: opacity .2s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active до версии 2.1.8 */ {
  opacity: 0;
}
//===============================================================================//
@media(any-hover: hover) {
  .button:hover{
    border-radius: 20px 10px;
  }
}
</style>