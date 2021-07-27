<template>
  <div class="posts-new">
    <img v-if="status" :src="`https://http.cat/${status}`" />
    <form v-on:submit.prevent="createPost()">
      <h1>New Post</h1>
      <ul>
        <li v-for="error in errors" v-bind:key="error">{{ error }}</li>
      </ul>
      Title:
      <input type="text" v-model="newPostParams.title" />
      Body:
      <input type="text" v-model="newPostParams.body" />
      Image:
      <input type="text" v-model="newPostParams.image" />
      <input type="submit" value="Create" />
    </form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      newPostParams: {},
      errors: [],
      status: "",
    };
  },
  created: function () {},
  methods: {
    createPost: function () {
      axios
        .post("/posts", this.newPostParams)
        .then((response) => {
          console.log("post create", response);
          this.$router.push("/posts");
        })
        .catch((error) => {
          console.log("post create error", error.response);
          this.status = error.response.status;
        });
    },
  },
};
</script>
