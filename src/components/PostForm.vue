<template>
  <form @submit.prevent>
    <h4>Створення поста</h4>
    <input v-bind:value="title" @input="title = $event.target.value" class="input" type="text" name="" placeholder="Назва">
    <textarea v-bind:value="body" @input="body = $event.target.value" class="textarea" name="" placeholder="Опис"></textarea>
    <button class="btn" >Створити</button>
  </form>
</template>

<script>
  export default {

  }
</script>

<style scoped>
form {
  display: grid;
  grid-gap: 15px;
  margin-bottom: 10px;
}
.input, .textarea {
  display: inline-block;
  width: 100%;
  border: 1px solid dodgerblue;
  padding: 10px 15px;
  resize: none;
}
.input, .textarea, .btn {
  border-radius: 5px;
}
.textarea {
  height: 110px;
}
.btn {
  display: block;
  padding: 10px 15px;
  background-color: transparent;
  border: 1px solid dodgerblue;
  color: dodgerblue;
  max-width: fit-content;
  width: 100%;
  margin-left: auto;
  transition: all .3s linear;
}
.btn:hover {
  background-color: dodgerblue;
  color: #fff;
}
</style>