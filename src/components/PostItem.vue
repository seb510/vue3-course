<template>
  <div class="post">
    <div>
      <div><strong>Назва: </strong>{{ post.title }}</div>
      <div><strong>Опис: </strong>{{ post.body }}</div>
    </div>
    <div class="post__btns">
      <my-button>Видалити</my-button>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      post: {
        type: Object,
        required: true,
      }
    }
  }
</script>

<style scoped>
.post {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 15px;
  border: 2px solid dodgerblue;
  border-radius: 5px;
}
.post strong {
  font-weight: 600;
}
.post:not(:last-child){
  margin-bottom: 15px;
}
</style>