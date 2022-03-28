<template>
  <div class="app">
    <my-header
      :cart-items="cartItems"
      :remove-cart-item="removeCartItem"
    />
    <main-page
        :cart-items="cartItems"
        :add-to-cart="addToCart"
    />
  </div>
</template>

<script>
import myHeader from "@/components/header/my-header";
import mainPage from "@/components/mainPage/main-page";


export default {
  name: 'App',
  components: {
    myHeader,
    mainPage
  },
  props: {
    productName: String,
  },
  data() {
    return {
      cartItems: [],
    }
  },
  methods: {
    removeCartItem(cartItem) {
      this.cartItems = this.cartItems.filter( (p) => { return cartItem.id !== p.id} )
    },
    addToCart(name) {
      this.cartItems = [...this.cartItems,{id: Date.now(),name}];
    }
  }
}
</script>

<style>

</style>
