<template>
  <div class="search-page max-w-xl mx-auto p-4 text-white w-full">
    <div class="search-box relative mb-4">
      <input
        v-model="query"
        type="text"
        placeholder="Поисковый запрос"
        class="w-full p-3 pl-10 bg-gray-800 rounded-lg outline-none text-white border border-gray-700 focus:border-gray-500"
      />
      <span class="absolute left-3 top-3 text-gray-400">🔍</span>
    </div>

    <div v-if="results.length === 0 && query" class="text-center mt-10 text-gray-400">
      Hech narsa topilmadi
    </div>

    <div class="results flex flex-col gap-2">
      <div
        v-for="user in results"
        :key="user._id"
        class="flex items-center gap-4 p-2 hover:bg-gray-900 rounded cursor-pointer transition-colors"
        @click="$router.push('/profile/' + user.username)"
      >
        <img
          :src="user.profilePic || 'https://via.placeholder.com/150'"
          alt=""
          class="w-12 h-12 rounded-full object-cover bg-gray-700"
        />
        <div>
          <h3 class="font-semibold text-sm">{{ user.username }}</h3>
          <p class="text-gray-400 text-xs">{{ user.fullName }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue';
import axios from 'axios';

const query = ref('');
const results = ref([]);

let timeout = null;
watch(query, (newVal) => {
  clearTimeout(timeout);
  timeout = setTimeout(async () => {
    if (newVal.trim()) {
      try {
        const res = await axios.get(`http://localhost:5000/api/users/search?q=${newVal}`);
        results.value = res.data;
      } catch (err) {
        console.error("Qidiruv xatosi:", err);
      }
    } else {
      results.value = [];
    }
  }, 500);
});
</script>
