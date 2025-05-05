<template>
  <div>
    <!-- Loading Screen -->
    <div v-if="isLoading" :class="{ 'fade-out': isFadingOut }"
      class="fixed inset-0 bg-black flex items-center justify-center z-50 transition-opacity duration-1000">
      <div class="flex flex-col items-center">
        <img src="/static/video/loading_spinner.gif" alt="Loading Content..." class="w-40 h-40 mb-4" />
        <div class="text-white text-4xl font-bold animate-pulse">Loading...</div>
      </div>
    </div>

    <!-- Main Content -->
    <div v-else :class="{ 'fade-in': !isLoading }">
      <NuxtPage />
    </div>
  </div>
</template>

<script setup>
import { onMounted } from 'vue';

const isLoading = ref(true);
const isFadingOut = ref(false);

onMounted(() => {
  setTimeout(() => {
    isFadingOut.value = true;
    setTimeout(() => {
      isLoading.value = false;
    }, 1000); // Wait for fade-out animation to complete
  }, 2500); // Simulate a 2.5-second loading time
});
</script>

<style scoped>
/* Smooth fade-out transition */
.fade-out {
  opacity: 0;
  transition: opacity 1s ease-in-out;
}

/* Add smooth transition for background and content */
.fade-in {
  opacity: 0;
  animation: fadeIn 2s forwards ease-in-out, backgroundColorChange 2s forwards ease-in-out;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
}

@keyframes backgroundColorChange {
  from {
    background-color: #000;
  }

  to {
    background-color: #050505;
  }
}
</style>
