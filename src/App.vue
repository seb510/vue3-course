<template>
  <div class="app">
    <h1>Сторінка з постами</h1>
    <my-input v-model="searchQuery" placeholder="Пошук..."/>
    <div class="app__btns">
      <my-button
          @click="showDialog"
          >Створити пост
      </my-button>
      <my-select v-model="selectedSort" :options="sortOptions" />
    </div>

    <my-dialog v-model:show="dialogVisible">
      <post-form  @create="createPost"/>
    </my-dialog>
    <post-list
        :posts="sortedAndSearchedPosts"
        @remove="removePost"
        v-if="!isPostsLoading"
    />
    <div v-else>Йде завантаження постів...</div>
    <div class="page__wrapper">
      <div class="page"
           v-for="pageNumber in totalPage"
           :key="pageNumber"
           :class="{
             'current-page' : page=== pageNumber
           }"
           @click="changePage(pageNumber)"
      >{{ pageNumber }}</div>
    </div>
  </div>
</template>

<script>
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import axios from "axios";
  export default {
    components: {
      PostForm, PostList
    },
    data() {
      return {
        posts: [],
        dialogVisible: false,
        isPostsLoading: false,
        selectedSort: '',
        searchQuery : '',
        page: 1,
        limit: 10,
        totalPage : 0,
        sortOptions: [
          {
            value: 'title', name: 'По назві'
          },
          {
            value: 'body', name: 'По змісту'
          }
        ]
      }
    },
    methods: {
      createPost(post) {
        this.posts.push(post);
        this.dialogVisible = false;
      },
      removePost(post) {
        this.posts = this.posts.filter(p => p.id !== post.id)
      },
      showDialog() {
        this.dialogVisible = true
      },
      changePage(pageNumber) {
        this.page = pageNumber
      },
      async fetchPost() {
        try {
          this.isPostsLoading = true;
          const response = await axios.get('https://jsonplaceholder.typicode.com/posts', {
            params: {
              _page: this.page,
              _limit : this.limit,
            }
          });
          this.totalPage = Math.ceil(response.headers['x-total-count'] / this.limit);
          this.posts = response.data;
        } catch (e) {
          alert('Помилка')
        } finally {
          this.isPostsLoading = false
        }
      },
    },
    mounted () {
      this.fetchPost();
    },
    computed: {
      sortedPosts() {
        return[...this.posts].sort((post1, post2) => post1[this.selectedSort]?.localeCompare(post2[this.selectedSort]))
      },
      sortedAndSearchedPosts () {
        return this.sortedPosts.filter(post => post.title.toLowerCase().includes(this.searchQuery.toLowerCase()))
      }
    },
    watch: {
      page() {
        this.fetchPost()
      }
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
    margin-bottom: .5em;
  }
  .app {
    padding: 20px;
  }
  .app__btns {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin: 15px 0;
  }
  .input, .textarea {
    display: inline-block;
    width: 100%;
    border: 1px solid dodgerblue;
    padding: 10px 15px;
    resize: none;
    border-radius: 3px;
  }

  .page__wrapper {
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: 15px;
  }
  .page {
    display: flex;
    align-items: center;
    justify-content: center;
    line-height: 1;
    padding: 10px;
    min-width: 35px;
    border: 1px solid black;
    cursor: pointer;
    transition: .3s linear;
  }
  .page:hover {
    border-color: dodgerblue;
    color: dodgerblue;
  }
  .current-page {
    background-color: dodgerblue;
    border-color: dodgerblue;
    color: #fff;
  }
  .page:not(:last-child) {
    margin-right: 10px;
  }
</style>