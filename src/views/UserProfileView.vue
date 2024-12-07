<template>
  <div class="container mt-5">
    <h1>User Profile</h1>
    <div v-if="error" class="alert alert-danger">{{ error }}</div>
    <div v-if="user" class="card">
      <div class="card-body">
        <h2 class="card-title">{{ user.name }}</h2>
        <img :src="user.imageUrl" alt="Profile Image" class="img-fluid" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: null,
      error: ''
    }
  },
  mounted() {
    const token = localStorage.getItem('token');
    if (!token) {
      this.$router.push('/login');
      return;
    }
    fetch('https://dummyjson.com/auth/me', {
      method: 'GET',
      headers: {
        'Authorization': `Bearer ${token}`
      }
    })
    .then(response => {
      if (!response.ok) {
        throw new Error('Invalid token');
      }
      return response.json();
    })
    .then(data => {
      this.user = data;
    })
    .catch(error => {
      this.error = error.message;
    });
  }
}
</script>

<style scoped>
/* Дополнительные стили, если нужно */
</style>