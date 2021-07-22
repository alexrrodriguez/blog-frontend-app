<template>
  <div class="posts-edit">
    <h1>Edit Post</h1>
    <form v-on:submit.prevent="updatePost(post)">
      <ul>
        <li v-for="error in errors" v-bind:key="error">{{ error }}</li>
      </ul>
      Title:
      <input type="text" v-model="post.title" />
      Body:
      <input type="text" v-model="post.body" />
      Image:
      <input type="text" v-model="post.image" />
      <input type="submit" value="Update" />
    </form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      post: {},
      errors: [],
    };
  },
  created: function () {
    axios.get("/posts/" + this.$route.params.id).then((response) => {
      console.log("posts show", response);
      this.post = response.data;
    });
  },
  methods: {
    updatePost: function (post) {
      var editPostParams = post;
      axios
        .patch("/posts/" + post.id, editPostParams)
        .then((response) => {
          console.log("post update", response);
          this.$router.push("/posts");
        })
        .catch((error) => {
          console.log("posts update error", error.response);
          this.errors = error.response.data.errors;
        });
    },
  },
};
</script>
