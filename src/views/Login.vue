<template>
  <div class="login-container">
    <div class="login-box">
      <h2>Instagram</h2>
      <p>Kirish sahifasi</p>
      <button @click="$router.push('/')">Bosh sahifaga o'tish</button>
    </div>
  </div>
</template>

<script setup>
// Login mantiqiy qismi keyinchalik yoziladi
</script>

<style scoped>
.login-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #000;
}

.login-box {
  background: #fff;
  padding: 40px;
  border-radius: 8px;
  text-align: center;
  color: #000;
}

button {
  margin-top: 20px;
  background: #0095f6;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  font-weight: bold;
}
</style>