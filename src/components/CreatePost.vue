<template>
  <form @submit.prevent="createPost">
    <div>
      <label for="userId">Post User Id</label>
      <input type="text" name="" id="userId" v-model="form.userId" />
    </div>
    <div>
      <label for="title">Post Title</label>
      <input type="text" name="" id="title" v-model="form.title" />
    </div>
    <div>
      <label for="body">Post Body</label>
      <input type="text" name="" id="body" v-model="form.body" />
    </div>
    <button type="submit">Create Post</button>
  </form>
</template>
<script setup>
import { reactive } from "vue";
import axios from "axios";
const form = reactive({
  userId: "",
  title: "",
  body: "",
});
const createPost = () => {
  axios
    .post("https://jsonplaceholder.typicode.com/posts", form)
    .then((response) => {
      console.log(response);
    })
    .catch((error) => {
      console.log(error);
    });
};
</script>
