<template>
  <div class="container mt-5">
    <h1>Login</h1>
    <form @submit.prevent="login">
      <div class="mb-3">
        <label for="email" class="form-label">Email</label>
        <input type="email" id="email" v-model="email" class="form-control" required />
      </div>
      <div class="mb-3">
        <label for="password" class="form-label">Password</label>
        <input type="password" id="password" v-model="password" class="form-control" required />
      </div>
      <button type="submit" class="btn btn-primary">Login</button>
      <p v-if="error" class="text-danger">{{ error }}</p>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: '1',
      password: '1',
      error: '',
      commonPassword: '1'  // Укажите здесь ваш общий пароль
    };
  },
  mounted() {
    // Получаем сохраненный email из локального хранилища и устанавливаем его в поле ввода
    const selectedEmail = localStorage.getItem('selectedEmail');
    if (selectedEmail) {
      this.email = selectedEmail;
    }
  },
  methods: {
    login() {
      // Проверяем общий пароль
      if (this.password !== this.commonPassword) {
        this.error = 'Invalid password. Please use the correct password.';
        return;
      }

      // Отправляем запрос на вход
      fetch('https://dummyjson.com/auth/login', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify({ username: this.email, password: this.commonPassword }) // Используем email в качестве имени пользователя
      })
      .then(response => {
        if (!response.ok) {
          throw new Error('Invalid username or credentials');
        }
        return response.json();
      })
      .then(data => {
        // Сохраняем токен в локальном хранилище
        localStorage.setItem('token', data.token);
        this.$router.push('/profile'); // Переход к профилю после успешного логина
      })
      .catch(error => {
        this.error = error.message; // Показываем сообщение об ошибке
      });
    }
  }
}
</script>

<style scoped>
/* Дополнительные стили, если нужно */
</style>