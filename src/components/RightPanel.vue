<template>
  <aside class="right-panel">
    <div class="current-user">
      <div class="user-info">
        <div class="avatar" style="background-color: darkblue;"></div>
        <div><span class="username">azyon.uz</span></div>
      </div>
      <button class="switch-btn">Переключиться</button>
    </div>

    <div class="suggestions-header">
      <span>Рекомендации для вас</span>
      <span class="see-all">Все</span>
    </div>

    <div class="suggestion-item" v-for="user in suggestions" :key="user.name">
      <div class="user-info">
        <div class="avatar"></div>
        <div>
          <span class="username">{{ user.name }}</span>
          <span class="subtext">Рекомендации для вас</span>
        </div>
      </div>
      <button class="follow-btn">Подписаться</button>
    </div>
  </aside>
</template>

<script setup>
const suggestions = [
  { name: 'Jvll___' },
  { name: 'Мансур' },
  { name: 'Ramziddin' },
  { name: 'Kamron | Full-Sta...' }
]
</script>

<style scoped>
.right-panel { width: 320px; padding: 20px; display: none; }
@media (min-width: 1000px) { .right-panel { display: block; } }
.current-user { display: flex; align-items: center; justify-content: space-between; margin-bottom: 20px; }
.switch-btn { color: var(--blue); font-size: 12px; font-weight: bold; background: none; border: none; cursor: pointer; }
.suggestions-header { display: flex; justify-content: space-between; color: var(--text-secondary); font-size: 14px; font-weight: bold; margin-bottom: 15px; }
.see-all { color: #fff; cursor: pointer; font-size: 12px; }
.suggestion-item { display: flex; align-items: center; justify-content: space-between; margin-bottom: 15px; }
.user-info { display: flex; align-items: center; }
.avatar { width: 32px; height: 32px; border-radius: 50%; background-color: #333; margin-right: 10px; }
.username { font-size: 14px; display: block; font-weight: bold; }
.subtext { font-size: 12px; color: var(--text-secondary); }
.follow-btn { color: var(--blue); font-weight: bold; font-size: 12px; background: none; border: none; cursor: pointer; }
</style>