<template>
  <div class="app">
    <post-form/>
    <post-list :posts="posts"/>
  </div>
</template>

<script>
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
  export default {
    components: {
      PostForm, PostList
    },
    data() {
      return {
        posts: [
          {id: 1, title : 'JavaScript', body: 'Опис поста'},
          {id: 2, title : 'VueJs', body: 'Опис Бібліотеки'},
          {id: 3, title : 'ReactJs', body: 'Опис Фреймворка'},
          {id: 4, title : 'SCSS Style', body: 'Опис Стилістики'},
        ],
        title: '',
        body: '',
      }
    },
    methods: {
      createPost() {
        const newPost = {
          id: Date.now(),
          title: this.title,
          body: this.body,
        }
        this.posts.push(newPost);
        this.title = '';
        this.body = '';
      },
    }
  }
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'OpenSans', sans-serif;
    font-weight: 400;
    line-height: 1.2;
  }
  h1, h2, h3, h4 ,h5, h6 {
    font-weight: 700;
  }
  .app {
    padding: 20px;
  }
</style>