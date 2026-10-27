<template>
  <div class="app-container">
    <!-- Chap menyu -->
    <aside class="sidebar">
      <h1 class="logo">Instagram</h1>
      <nav>
        <router-link to="/" class="nav-item">🏠 Главная</router-link>
        <router-link to="/reels" class="nav-item">🎬 Reels</router-link>
        <router-link to="/search" class="nav-item">🔍 Поиск</router-link>
        <router-link to="/profile/me" class="nav-item">👤 Профиль</router-link>
      </nav>
    </aside>

    <!-- O'ng tomon (Sahifalar shu yerda ochiladi) -->
    <main class="main-content">
      <router-view></router-view> 
    </main>
  </div>
</template>

<script setup>
</script>

<style>
body {
  margin: 0;
  padding: 0;
  background-color: #000;
  color: #fff;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
}

.app-container { display: flex; min-height: 100vh; }

.sidebar {
  width: 250px;
  border-right: 1px solid #262626;
  padding: 20px;
  position: fixed;
  height: 100vh;
  box-sizing: border-box;
}

.logo { font-family: cursive; font-size: 28px; margin-bottom: 40px; margin-top: 10px; }

.nav-item {
  display: block;
  color: #fff;
  text-decoration: none;
  font-size: 16px;
  padding: 12px 0;
  margin-bottom: 5px;
  transition: 0.2s;
}

.nav-item:hover { font-weight: bold; }

.main-content {
  margin-left: 250px;
  flex: 1;
  padding: 20px;
  display: flex;
  justify-content: center;
}
</style>