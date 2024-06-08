<template>
  <form @submit.prevent>
    <h4>Створення поста</h4>
    <input v-model="post.title" class="input" type="text" name="title" placeholder="Назва">
    <textarea v-model="post.body" class="textarea" name="body" placeholder="Опис"></textarea>
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
    }
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
.input, .textarea {
  border-radius: 3px;
}
.textarea {
  height: 110px;
}
</style>