<template>
  <textarea class="textarea" :value="modelValue" @input="updateInput"></textarea>

</template>

<script>
  export default {
    name: 'my-textarea',
    props: {
      modelValue: [String, Number]
    },
    methods: {
      updateInput(event) {
        this.$emit('update:modelValue', event.target.value)
      }
    }
  }
</script>

<style scoped>
.textarea {
  height: 110px;
}
</style>