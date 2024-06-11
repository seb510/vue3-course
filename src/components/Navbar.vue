<template>
  <div class="navbar">
    <div @click="$router.push('/')">
      Vue 3
    </div>
    <div class="navbar__btns">
      <my-button @click="$router.push('/posts')">Пости</my-button>
      <my-button @click="$router.push('/about')">Про сайт</my-button>
    </div>
  </div>
</template>

<script>
export default {
  setup() {


    return {}
  }
}
</script>

<style scoped>
  .navbar {
    height: 50px;
    background-color: #dbdbdb;
    box-shadow: 2px 2px 4px #bab7b7;
    display: flex;
    align-items: center;
    padding: 0 15px;
  }
  .navbar__btns {
    display: flex;
    align-items: center;
    margin-left: auto;
  }
  .navbar__btns >*:first-child {
    margin-right: 20px;
  }
</style>