<template>
  <div class="container mt-5">
    <h1>Users</h1>
    <ul class="list-group">
      <li class="list-group-item" v-for="user in users" :key="user.id">
        <span @click="selectUser(user.email)" style="cursor: pointer;">{{ user.name }} - {{ user.email }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: []
    }
  },
  mounted() {
    fetch('https://dummyjson.com/users')
      .then(response => response.json())
      .then(data => {
        this.users = data.users;
      });
  },
  methods: {
    selectUser(email) {
      // Сохраняем email в локальном хранилище и перенаправляем на страницу логина
      localStorage.setItem('selectedEmail', email);
      this.$router.push('/login'); // Переход к странице логина
    }
  }
}
</script>

<style scoped>

</style>
