<template>
  <div
      v-if="show"
      @click="hideCart"
      class="cart">
    <div
        @click.stop
        class="cart__wrapper">
      <ul
          v-if="cartItems.length > 0"
          class="cart__list">
        <li
            v-for="cartItem in cartItems"
            :key="cartItem"
            class="cart__item">
          {{ cartItem.name }}
          <my-button
              @click="$emit('remove', cartItem)"
              class="cart__button"
              textButton="Удалить"/>
        </li>
      </ul>
      <div
          v-else
      >Корзина пуста</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'my-cart',
  components: {},
  props: {
    cartItems: {
      type: Array,
      default: () => [],
    },
    show: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    hideCart() {
      this.$emit('update:show', false)
    }
  }
}
</script>

<style lang="scss">
.cart{
  padding: 20px 0 0 0;
  width: 300px;
  height: auto;
  position: absolute;
  top: 100%;
  right: 0;
  z-index: 5;
  &__wrapper{
    padding: 20px;
    background-color: #fff;
    box-shadow: 0 0 20px rgb(0 0 0 / 15%);
    border-radius: 6px;
    color: #2e2e2e;
  }
  &__item{
    display: flex;
    align-items: center;
    justify-content: space-between;
    color: #474747;
    &:not(:last-child) {
      margin-bottom: 15px;
    }
  }
  &__button{
    background: none;
    border: none;
    color: red;
    cursor: pointer;
    position: relative;
    &:before{
      content: '';
      position: absolute;
      bottom: 0;
      left: 0;
      height: 1px;
      width: 0;
      background: red;
      transition: width .2s ease-in-out;
    }
  }
}
@media(any-hover: hover) {
  .cart__button:hover:before{
    width: 100%;
  }
}
</style>