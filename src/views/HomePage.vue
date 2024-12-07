<template>
  <div class="container">
    <header class="header">
      <div class="logo">
        <h1>Home</h1>
      </div>
    </header>
    <main class="main">
      <div class="content">
        <div class="text-section">
          <h2>Home page</h2>
          <p>
            Amet minim mollit non deserunt ullamco est sit aliqua dolor do amet sint.
            Velit officia consequat duis enim velit mollit. Exercitation veniam
            consequat sunt nostrud amet.
          </p>
          <router-link to="/login" class="button">Authorization</router-link>
        </div>
        <img src="../assets/image.png" alt="Tools icon" class="image" />
      </div>
    </main>
    <footer class="footer">
      <p class="copyright">Copyright ©2020 All rights reserved</p>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'HomePage',
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  font-family: sans-serif;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #f8f9fa;
  padding: 20px;
}

.main {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
}

.content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 800px; /* Ограничение ширины контента */
  width: 100%;
}

.text-section {
  max-width: 400px; /* Ограничение ширины текстового блока */
  text-align: left; /* Текст слева */
}

.image {
  max-width: 300px; /* Ширина изображения */
  height: auto; /* Автоматическая высота */
}

.button {
  margin-top: 20px;
  padding: 10px 20px;
  background-color: #ff6f61;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none; /* Убирает подчеркивание */
}

.button:hover {
  background-color: #ff3b30;
}

.footer {
  background-color: #f8f9fa;
  text-align: center;
  padding: 20px 10px 10px; /* Изменены отступы */
}

.copyright {
  margin-top: 5px; /* Добавлен отступ сверху */
}
</style>