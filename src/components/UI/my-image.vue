<template>
  <img :src="requireImage(image)"  :alt="alt">
</template>

<script>
export const images = {
  [`airpods`]: `image/main_page/airpods.jpg`,
  [`bicycle`]: `image/main_page/bicycle.jpg`,
  [`board`]: `image/main_page/board.jpg`,
  [`headphones`]: `image/main_page/headphones.jpg`,
  [`radio`]: `image/main_page/radio.jpg`,
  [`scooter`]: `image/main_page/scooter.jpg`,
  [`toothbrush`]: `image/main_page/toothbrush.jpg`,
}
export default {
  name: 'my-image',
  props: {
    image: {
      type:String,
    },
    alt:String,
  },
  methods: {
    requireImage(link) {
      return require(`@/assets/${link}`);
    }
  }
}
</script>

<style scoped>

</style>