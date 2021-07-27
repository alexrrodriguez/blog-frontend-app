<template>
  <div id="app">
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <div class="container-fluid">
        <a class="navbar-brand" href="/">Blog App</a>
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="/posts">All Posts</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="/posts/new">New Posts</a>
            </li>
            <li class="nav-item dropdown">
              <a
                class="nav-link dropdown-toggle"
                href="#"
                id="navbarDropdown"
                role="button"
                data-bs-toggle="dropdown"
                aria-expanded="false"
              >
                Login/Logout
              </a>
              <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
                <li><a class="dropdown-item" v-if="!isLoggedIn()" href="/login">Login</a></li>
                <li><a class="dropdown-item" v-if="!isLoggedIn()" href="/signup">Signup</a></li>
                <li><hr class="dropdown-divider" /></li>
                <li><a class="dropdown-item" v-if="isLoggedIn()" href="/logout">Logout</a></li>
              </ul>
            </li>
            <li class="nav-item">
              <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">Disabled</a>
            </li>
          </ul>
          <form class="d-flex">
            <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" />
            <button class="btn btn-outline-success" type="submit">Search</button>
          </form>
        </div>
      </div>
    </nav>

    <!-- <div class="navlist" id="nav">
      <li>
        <router-link to="/">Home</router-link>
      </li>
      |
      <li>
        <router-link to="/test">Test</router-link>
      </li>
      |
      <li>
        <router-link to="/about">About</router-link>
      </li>
      |
      <li v-if="!isLoggedIn()">
        <router-link to="/signup">Signup</router-link>
      </li>
      |
      <li v-if="!isLoggedIn()">
        <router-link to="/login">Login</router-link>
      </li>
      |
      <li v-if="isLoggedIn()">
        <router-link to="/logout">Logout</router-link>
      </li>
      |
      <li>
        <router-link to="/posts">All Posts</router-link>
      </li>
      |
      <li>
        <router-link to="/posts/new">New Post</router-link>
      </li>
    </div> -->
    <router-view />
  </div>
</template>

<style>
body {
  font-family: Lucida Bright, Georgia, serif !important;
  background-image: url("./assets/double-bubble-outline.png");
}
.navbar {
  text-align: center;
}
</style>

<script>
export default {
  methods: {
    isLoggedIn: function () {
      if (localStorage.getItem("jwt")) {
        return true;
      } else {
        return false;
      }
    },
  },
};
</script>
