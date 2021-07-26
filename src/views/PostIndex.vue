<template>
  <div class="posts-index">
    <h1>All Posts</h1>
    <div class="card" style="width: 18rem" v-for="post in posts" v-bind:key="post.id">
      <img v-bind:src="post.image" alt="post.title" class="card-img-top" />
      <div class="card-body">
        <h5 class="card-title">{{ post.title }}</h5>
        <p class="card-text">
          {{ post.body }}
        </p>
        <a href="#" class="btn btn-primary">Go somewhere</a>
      </div>
    </div>
    <div v-for="post in posts" v-bind:key="post.id">
      <router-link v-bind:to="`/posts/${post.id}`">
        <h2>{{ post.title }}</h2>
        <p>{{ post.body }}</p>
        <img v-bind:src="post.image" alt="post.title" />
      </router-link>
    </div>
  </div>
</template>

<style>
body {
  font-family: Lucida Bright, Georgia, serif;
}
</style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      posts: [],
    };
  },
  created: function () {
    this.indexPosts();
  },
  methods: {
    indexPosts: function () {
      axios.get("/posts").then((response) => {
        console.log("posts index", response);
        this.posts = response.data;
      });
    },
  },
};
</script>
