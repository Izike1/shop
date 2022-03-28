<template>
  <div class="container">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'my-container'
}
</script>

<style scoped>
.container{
  max-width: 1330px;
  padding: 0 15px;
  margin: 0 auto;
  width: 100%;
}
</style>