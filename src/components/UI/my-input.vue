<template>
  <input
      :value="modelValue"
      @input="updateValue"
      class="input"
      type="text"
      name="input"
  >
</template>

<script>
export default {
  name: "my-input",
  props: {
    modelValue: [String,Number]
  },
  methods: {
    updateValue(event) {
      this.$emit('update:modelValue', event.target.value)
    }
  }
}
</script>

<style lang="scss">
.input{
  padding: 10px;
  width: 100%;
  outline: none;
  border-bottom: 1px solid #474747;
  background: url('@/assets/image/main_page/icons/search-outline.svg') right no-repeat;
  &::placeholder{
   transition: opacity .2s linear;
   font-size: 14px;
    &:focus{
      opacity: 0;
    }
  }
}
</style>