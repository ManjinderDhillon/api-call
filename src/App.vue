<template>
  <PostList />
  <CreatePost />
</template>

<script setup>
import PostList from "./components/PostList.vue";
import CreatePost from "./components/CreatePost.vue";
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
