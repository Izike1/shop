<template>
  <div class="category">
    <div class="category__wrapper">
      <ul class="category__list">
        <li
            @click="updateCategory"
            v-for="categoryItem in categoryItems"
            :key="categoryItem"
            class="category__item">
            {{ categoryItem.name }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'my-category',
  props: {
    categoryItems: {
      type: Array,
      default: () => [],
    },
  },
}
</script>

<style lang="scss">
.category{
  height: auto;
  display: flex;
  flex-direction: column;

  &__wrapper{
    padding: 20px 0;
    background-color: #474747;
    width: 350px;
  }
  &__item{
    padding: 15px;
    transition: background-color .2s linear;
    cursor: pointer;
  }
}
@media(any-hover: hover) {
  .category__item:hover{
    background-color: darken(#474747, 10%)
  }
}
</style>