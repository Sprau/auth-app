<template>
  <div id="app">
    <nav>
      <div class="nav-links">
        <router-link to="/home">Home</router-link>
        <router-link to="/users">Users</router-link>
        <router-link to="/login">Login</router-link>
        <router-link to="/profile">Profile</router-link>
      </div>
    </nav>
    <router-view />
  </div>
</template>

<script>
export default {
  name: 'App',
};
</script>

<style>
nav {
  margin-bottom: 1px;
  display: flex;
  justify-content: flex-end; /* Выравнивание по правой стороне */
}

.nav-links {
  display: flex;
}

nav a {
  margin-right: 60px;
}
</style>