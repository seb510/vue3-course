<template>
  <div class="post">
    <div>
      <div><strong>ID: </strong>{{ post.id }}</div>
      <div><strong>Назва: </strong>{{ post.title }}</div>
      <div><strong>Опис: </strong>{{ post.body }}</div>
    </div>
    <div class="post__btns">
      <my-button @click="$router.push(`/posts/${post.id}`)">Відкрити</my-button>
      <my-button @click="$emit('remove', post)">Видалити</my-button>
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
.post__btns {
  display: flex;
  align-items: center;
  margin-left: 10px;
  flex-shrink: 0;
}
.post__btns >*:first-child{
  margin-right: 5px;
}
</style>