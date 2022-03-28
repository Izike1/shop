<template>
    <div class="product__item">
      <div class="product__image">
        <my-image :image="image" alt="airpods"/>
      </div>
      <div class="product__description">
        <a href="#" class="product__title">{{ productName }}</a>
        <div class="product__sub-description">
          <div class="product__text">{{ productDescription }}</div>
          <div class="product__price rub">{{ productPrice }}</div>
        </div>
        <my-button
            @click="addToCart(productName)"
            class="product__btn"
            textButton="Добавить в корзину"/>
      </div>
    </div>
</template>

<script>
export default {
  name: 'my-product',
  components: {},

  props: {
    image: {
      type:String
    },
    cartItems: {
      type: Array,
      default: () => [],
    },
    addToCart: Function,
    productName:String,
    productDescription:String,
    productPrice: Number
  },
  methods: {
  }
}
</script>

<style lang="scss">
.product{
  gap: 30px;
  flex-wrap: wrap;
  &__item{
    flex: 0 1 25%;

  }
  &__image{
    position: relative;
    width: 270px;
    height: 270px;
    margin: 0 0 10px 0;
    img{
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }
  &__title{
    font-size: 21px;
    line-height: 150%;
    color: #2e2e2e;
    &:not(:last-child){
      margin: 0 0 5px 0;
    }
  }
  &__text{
    font-size: 16px;
    line-height: 130%;
    color: #2e2e2e;
    margin: 0 5px 0 0;
  }
  &__price{
    color: #ff6f00;
    font-size: 18px;
  }
  &__sub-description{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 0 0 10px 0;
  }
  &__btn{
    color: #2e2e2e;
    cursor: pointer;
    transition: color .3s linear;
  }
}
@media(any-hover: hover){
  .product__title:hover{
    text-decoration: underline;
  }
  .product__btn:hover{
    color: #ff6f00;
  }
}
</style>