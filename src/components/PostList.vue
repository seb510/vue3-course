<template>
  <div v-if="posts.length > 0">
     <h3>Список постів</h3>
    <transition-group name="post-list">
      <post-item
          v-for="post in posts"
          :post="post"
          :key="post.id"
          @remove="$emit('remove', post)"
      />
    </transition-group>
  </div>
  <h3 v-else style="color: red">
    Список постів порожній
  </h3>
</template>

<script>
  import PostItem from "@/components/PostItem.vue";

  export default {
    components: {PostItem},
    props: {
      posts: {
        type: Array,
        required: true
      }
    }
  }
</script>

<style scoped>
.post-list-item {
  display: inline-block;
  margin-right: 10px;
}
.post-list-enter-active,
.post-list-leave-active {
  transition: all .3s ease;
}
.post-list-enter-from,
.post-list-leave-to {
  opacity: 0;
  transform: translateX(130px);
}
.post-list-move {
  transition: transform .3s ease;
}
</style>