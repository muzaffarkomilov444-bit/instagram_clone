<template>
  <aside class="sidebar">
    <div class="logo">Instagram</div>
    <div class="menu-item active"><i class="fa-solid fa-house"></i> Главная</div>
    <div class="menu-item"><i class="fa-solid fa-clapperboard"></i> Reels</div>
    <div class="menu-item"><i class="fa-regular fa-paper-plane"></i> Сообщения</div>
    <div class="menu-item"><i class="fa-solid fa-magnifying-glass"></i> Поисковый запрос</div>
    <div class="menu-item"><i class="fa-regular fa-heart"></i> Уведомления</div>
    <div class="menu-item"><i class="fa-solid fa-square-plus"></i> Создать</div>
    <div class="menu-item"><i class="fa-solid fa-chart-pie"></i> Панель</div>
    <div class="menu-item"><i class="fa-regular fa-circle-user"></i> Профиль</div>
  </aside>
</template>

<style scoped>
.sidebar {
    width: 250px;
    padding: 20px 12px;
    border-right: 1px solid var(--border-color);
    height: 100vh;
    position: sticky;
    top: 0;
    display: flex;
    flex-direction: column;
}
.logo {
    font-size: 24px;
    font-weight: bold;
    margin-bottom: 30px;
    padding-left: 12px;
    font-family: cursive;
}
.menu-item {
    display: flex;
    align-items: center;
    padding: 12px;
    margin-bottom: 5px;
    border-radius: 8px;
    cursor: pointer;
    font-size: 15px;
    transition: background 0.2s;
}
.menu-item:hover { background-color: #1a1a1a; }
.menu-item.active { font-weight: bold; }
.menu-item i { margin-right: 15px; font-size: 20px; width: 24px; text-align: center; }
</style>