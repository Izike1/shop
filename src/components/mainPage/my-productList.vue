<template>
  <div class="product">
    <my-product
        v-for="product in dbProducts"
        :key="product.id"
        :image="product.image"
        :product-name="product.name"
        :product-description="product.description"
        :product-price="product.price"
        :add-to-cart="addToCart"
    />
  </div>
</template>

<script>
const {images} = require( '@/components/UI/my-image.vue');


export default {
  name: 'my-productList',
  props: {
    addToCart: Function,
    dbProducts:{
      type: Array,
      default: () => [],
    }
  },
  data() {
    return{
      images
    }
  }
}
</script>

<style lang="scss">
.product{
  margin: 0 0 0 15px;
  display: flex;
}
</style>