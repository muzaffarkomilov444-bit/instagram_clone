<template>
  <div class="reels-container h-screen overflow-y-scroll snap-y snap-mandatory bg-black flex justify-center">
    <div
      v-for="reel in reels"
      :key="reel._id"
      class="relative h-screen w-full max-w-sm snap-start flex items-center justify-center bg-gray-900 border-x border-gray-800"
    >
      <video
        :src="reel.mediaUrl"
        autoplay
        loop
        muted
        playsinline
        class="h-full w-full object-cover"
      ></video>
      
      <!-- Video ustidagi ma'lumotlar -->
      <div class="absolute bottom-10 left-4 text-white w-full pr-16">
        <div class="flex items-center gap-3 mb-3">
          <img :src="reel.user?.profilePic || 'https://via.placeholder.com/150'" class="w-10 h-10 rounded-full bg-gray-700 object-cover" alt="" />
          <span class="font-semibold text-sm">{{ reel.user?.username || 'Foydalanuvchi' }}</span>
          <button class="border border-white px-3 py-1 rounded-md text-xs font-semibold hover:bg-white hover:text-black transition">Подписаться</button>
        </div>
        <p class="text-sm">{{ reel.caption }}</p>
      </div>

      <!-- O'ng tomondagi tugmalar -->
      <div class="absolute right-3 bottom-12 flex flex-col items-center gap-5 text-white">
        <button class="hover:text-red-500 transition-colors text-3xl drop-shadow-lg">❤️</button>
        <button class="hover:text-gray-400 transition-colors text-3xl drop-shadow-lg">💬</button>
        <button class="hover:text-gray-400 transition-colors text-3xl drop-shadow-lg">✈️</button>
      </div>
    </div>
    
    <div v-if="reels.length === 0" class="text-white mt-20 text-center">Reels topilmadi. Backendga video qo'shing.</div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const reels = ref([]);

onMounted(async () => {
  try {
    // Agar backend hali tayyor bo'lmasa, xato bermasligi uchun try/catch
    const res = await axios.get('http://localhost:5000/api/posts?isReel=true');
    reels.value = res.data;
  } catch (error) {
    console.error("Reels yuklashda xato:", error);
  }
});
</script>
const res = await axios.get('http://localhost:5000/api/posts?isReel=true');