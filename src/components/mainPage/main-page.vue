<template>
  <main class="page">
    <my-container>
      <div class="page__action">
        <my-input
          v-model="searchQuery"
        />
        <my-select
          v-model="selectedSort"
          :options="sortOptions"
        />
      </div>
      <div class="page__body">
        <my-category
            :category-items="categoryItems"
        />
        <div class="product">
          <my-product-list
              :db-products="searchProduct"
              :add-to-cart="addToCart"
          />
        </div>
      </div>
    </my-container>
  </main>
</template>

<script>
const {dbProducts} = require('@/db-products.js');
import myProductList from "@/components/mainPage/my-productList";
import myCategory from "@/components/mainPage/my-category";

export default {
  name: 'main-page',
  components: {
    myCategory,
    myProductList
  },
  props: {
    addToCart: Function,
  },
  data() {
    return{
      dbProducts,
      categoryItems: [
        {id:1, name: 'Гарнитура'},
        {id:2, name: 'Радио'},
        {id:3, name: 'Зубная щётка'},
        {id:4, name: 'Скутер'},
        {id:5, name: 'Ноутбук'},
        {id:6, name: 'Скейт'},
      ],
      selectedSort:'',
      searchQuery:'',
      sortOptions: [
        {value: 'increases', name:'По возрастанию'},
        {value: 'decreasing', name:'По убыванию'},
      ]
    }
  },
  methods:{
  },
  computed: {
    sortedProduct() {
      return [...this.dbProducts].sort((product1, product2) => {
         switch (this.selectedSort) {
          case this.sortOptions[0].value :
            return product1.price > product2.price? 1: -1;
          case this.sortOptions[1].value :
            return product1.price < product2.price? 1: -1;
          default: return 1;
         }
      })
    },
    searchProduct(){
      return this.sortedProduct.filter(dbProducts => dbProducts.name.toLowerCase().includes(this.searchQuery.toLowerCase()))
    },
  }
}
</script>

<style lang="scss">
.page{
  flex: 1 1 auto;
  &__body{
    display: flex;
  }
  &__action{
    padding: 20px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 0 0 10px 0;
    gap: 50px;
  }
}
</style>