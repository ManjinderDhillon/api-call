<template>
  <div>
    <button @click="getPosts">Load Posts</button>
    <h3 v-if="errorMessage">{{ errorMessage }}</h3>
    <div v-for="post in posts" :key="post.id">
      <h3>{{ post.id }} {{ post.title }}</h3>
      <p>{{ post.body }}</p>
      <button @click="deletePost(post.id)">Delete Post</button>
      <hr />
    </div>
  </div>
</template>

<script setup>
import axios from "axios";
import { ref } from "vue";
const posts = ref([]);
const errorMessage = ref("");
const getPosts = () => {
  axios
    .get("https://jsonplaceholder.typicode.com/posts")
    .then((response) => {
      posts.value = response.data;
    })
    .catch(() => {
      errorMessage.value = "Error Retrieving Data";
    });
};
const deletePost = (postId) => {
  axios
    .delete(`https://jsonplaceholder.typicode.com/posts/${postId}`)
    .then(() => {
      posts.value = posts.value.filter((post) => post.id !== postId);
    })
    .catch(() => {
      errorMessage.value = "Error Deleting Post";
    });
};
</script>
