<template>
  <div class="posts-show">
    <h2>{{ post.title }}</h2>
    <p>Body: {{ post.body }}</p>
    <img v-bind:src="post.image" alt="post.title" />
    <router-link v-bind:to="`/posts/${post.id}/edit`">Edit post</router-link>
    <button v-on:click="destroyPost(post)">Destroy post</button>
    <router-link to="/posts">Back to all posts</router-link>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      post: {},
    };
  },
  created: function () {
    axios.get("/posts/" + this.$route.params.id).then((response) => {
      console.log("posts show", response);
      this.post = response.data;
    });
  },
  methods: {
    destroyPost: function (post) {
      axios.delete("/posts/" + post.id).then((response) => {
        console.log("post destroy", response);
        this.$router.push("/posts");
      });
    },
  },
};
</script>
