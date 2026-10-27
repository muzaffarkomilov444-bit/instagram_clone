<template>
  <div class="post">
    <div class="post-header">
      <div class="user-info">
        <div class="avatar" :style="{ backgroundColor: avatarColor }"></div>
        <span class="username">{{ username }}</span>
        <span class="time">• {{ time }}</span>
      </div>
      <button class="follow-btn">Подписаться</button>
    </div>
    
    <!-- Rasm qismi -->
    <div class="post-image">
      <img v-if="imageUrl" :src="imageUrl" alt="post image" />
      <h2 v-else>Rasm o'rni (Vakansiya KASSIR)</h2>
    </div>

    <!-- Ikonkalar -->
    <div class="post-actions">
      <div class="actions-left">
        <span><i class="fa-regular fa-heart"></i></span>
        <span><i class="fa-regular fa-comment"></i></span>
        <span><i class="fa-regular fa-paper-plane"></i></span>
      </div>
      <div class="actions-right">
        <span><i class="fa-regular fa-bookmark"></i></span>
      </div>
    </div>
    <div class="likes">{{ likes }} layk</div>
  </div>
</template>

<script setup>
defineProps({
  username: String,
  time: String,
  likes: Number,
  avatarColor: { type: String, default: '#333' },
  imageUrl: { type: String, default: '' } // Rasm manzili uchun
})
</script>

<style scoped>
.post { border-bottom: 1px solid var(--border-color); padding-bottom: 20px; margin-bottom: 20px; }
.post-header { display: flex; align-items: center; justify-content: space-between; padding: 10px 0; }
.user-info { display: flex; align-items: center; }
.avatar { width: 32px; height: 32px; border-radius: 50%; margin-right: 10px; }
.username { font-weight: bold; font-size: 14px; margin-right: 5px; }
.time { color: var(--text-secondary); font-size: 14px; }
.follow-btn { color: var(--blue); font-weight: bold; font-size: 14px; background: none; border: none; cursor: pointer; }
.post-image { 
    width: 100%; 
    border-radius: 4px; 
    border: 1px solid var(--border-color); 
    background-color: #fff; 
    min-height: 400px; 
    display: flex; 
    align-items: center; 
    justify-content: center; 
    color: #000; 
    overflow: hidden; 
}
.post-image img { width: 100%; height: auto; display: block; object-fit: cover; }
.post-actions { display: flex; justify-content: space-between; padding: 10px 0; font-size: 24px; }
.actions-left span { margin-right: 15px; cursor: pointer; }
.actions-right span { cursor: pointer; }
.likes { font-weight: bold; font-size: 14px; margin-bottom: 5px; }
</style>