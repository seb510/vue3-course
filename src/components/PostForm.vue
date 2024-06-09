<template>
  <form @submit.prevent>
    <h4>Створення поста</h4>
    <my-input v-model="post.title" type="text" name="title" placeholder="Назва"/>
    <my-textarea v-model="post.body" name="body" placeholder="Опис"></my-textarea>
    <my-button class="btn" @click="createPost">Створити</my-button>
  </form>
</template>

<script>
  export default {
    data () {
      return {
        post: {
          title: '',
          body: '',
        }
      }
    },
    methods: {
      createPost () {
        this.post.id = Date.now()
        this.$emit('create', this.post)
        this.post = {
          title: '',
          body: '',
        }
      }
    },
  }
</script>

<style scoped>
form {
  display: grid;
  grid-gap: 15px;
  margin-bottom: 10px;
}

form .btn {
  margin-left: auto;
}
form h4 {
  margin-bottom: 0;
}

</style>