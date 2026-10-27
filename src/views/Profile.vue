<template>
  <div v-if="user" class="profile-page max-w-4xl mx-auto p-4 text-white">
    <!-- Profil Header -->
    <div class="flex flex-col md:flex-row items-center md:items-start gap-10 mb-10 mt-5">
      <img
        :src="user.profilePic || 'https://via.placeholder.com/150'"
        class="w-32 h-32 md:w-40 md:h-40 rounded-full object-cover bg-gray-700 border-2 border-gray-600 p-1"
        alt="avatar"
      />
      
      <div class="text-center md:text-left">
        <div class="flex items-center justify-center md:justify-start gap-5 mb-4">
          <h2 class="text-2xl font-light">{{ user.username }}</h2>
          <button class="bg-gray-800 px-4 py-1.5 rounded-lg font-semibold hover:bg-gray-700 transition-colors text-sm">
            Редактировать профиль
          </button>
        </div>
        
        <div class="flex justify-center md:justify-start gap-8 mb-4 text-sm">
          <span><strong>{{ posts.length }}</strong> публикаций</span>
          <span><strong>{{ user.followers?.length || 0 }}</strong> подписчиков</span>
          <span><strong>{{ user.following?.length || 0 }}</strong> подписок</span>
        </div>
        
        <div class="text-sm">
          <h1 class="font-semibold">{{ user.fullName }}</h1>
          <p class="text-gray-400">{{ user.bio || 'Bio yoq' }}</p>
        </div>
      </div>
    </div>

    <!-- Postlar Grid -->
    <div class="grid grid-cols-3 gap-1 md:gap-4">
      <div
        v-for="post in posts"
        :key="post._id"
        class="relative aspect-square group cursor-pointer overflow-hidden bg-gray-800 rounded-sm"
      >
        <img :src="post.mediaUrl || 'https://via.placeholder.com/300'" alt="post" class="w-full h-full object-cover" />
        <div class="absolute inset-0 bg-black bg-opacity-50 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity">
          <span class="text-white font-bold mr-4 text-sm">❤️ {{ post.likes?.length || 0 }}</span>
        </div>
      </div>
    </div>
  </div>
  <div v-else class="text-white text-center mt-20">Yuklanmoqda...</div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { useRoute } from 'vue-router';
import axios from 'axios';

const route = useRoute();
const user = ref(null);
const posts = ref([]);

onMounted(async () => {
  try {
    const username = route.params.username;
    // Backenddan profil ma'lumotlarini olish
    const res = await axios.get(`http://localhost:5000/api/users/profile/${username}`);
    user.value = res.data.user;
    posts.value = res.data.posts;
  } catch (error) {
    console.error("Profilni yuklashda xato:", error);
    // Xato bo'lsa ham dastur qulamasligi uchun soxta ma'lumot
    user.value = { username: route.params.username, fullName: "Xato yuz berdi", followers: [], following: [] };
  }
});
</script>
onst res = await axios.get(`http://localhost:5000/api/users/profile/${username}`);