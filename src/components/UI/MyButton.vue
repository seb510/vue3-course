<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
  export default {
    name: 'my-button'
  }
</script>

<style scoped>
.btn {
  display: block;
  padding: 10px 15px;
  border-radius: 5px;
  background-color: transparent;
  border: 1px solid dodgerblue;
  color: dodgerblue;
  max-width: fit-content;
  width: 100%;
  transition: all .3s linear;
  cursor: pointer;
}
.btn:hover {
  background-color: dodgerblue;
  color: #fff;
}
</style>