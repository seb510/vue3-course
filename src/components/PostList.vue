<template>
  <div class="post" v-for="post in posts">
    <div><strong>Назва: </strong>{{ post.title }}</div>
    <div><strong>Опис: </strong>{{ post.body }}</div>
  </div>
</template>

<script>
  export default {

  }
</script>

<style scoped>
.post {
  padding: 15px;
  border: 2px solid dodgerblue;
  border-radius: 7px;
}
.post strong {
  font-weight: 600;
}
.post:not(:last-child){
  margin-bottom: 15px;
}
</style>