<template>
  <navbar></navbar>
  <div class="app">
    <router-view></router-view>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";

export default {
  components: {Navbar},
  setup() {


    return {}
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
</style>