<template>
  <section class="relative w-full h-screen flex justify-center bg-black text-white overflow-hidden">
    <div class="absolute inset-0">
      <video autoplay loop muted playsinline controlslist="nodownload" disablePictureInPicture
        oncontextmenu="return false" class="w-full h-full object-cover">
        <source src="/static/video/ocean.mp4" type="video/mp4" />
      </video>
      <div class="absolute inset-0 bg-gradient-to-b from-black via-transparent to-black opacity-80"></div>
    </div>

    <div class="relative z-10 flex flex-col items-center max-w-4xl px-8 self-center">
      <h1 class="text-7xl font-light mb-8 tracking-widest leading-relaxed text-center">
        <span class="block font-thin mb-2">SYAHDAN</span>
        <span class="text-green-400 font-medium">MICOY NAZERA</span>
        <span class="block text-4xl mt-4 font-light">FX TD</span>
      </h1>
      <div class="w-24 h-1 bg-green-400 mb-8"></div>
      <div class="flex gap-6">
        <button @click="showPlayer = true"
          class="px-8 py-3 bg-green-400 text-black font-medium rounded-lg hover:bg-green-500 transition-colors">
          Demoreel
        </button>
        <a href="https://drive.google.com/file/d/1x7k1ZPQDQHH-UO5-3iNLw4kky34nnw23/view?usp=sharing" target="_blank"
          rel="noopener noreferrer"
          class="px-8 py-3 bg-green-400 text-black font-medium rounded-lg hover:bg-green-500 transition-colors">
          Resume
        </a>

      </div>
    </div>

    <!-- Vimeo Modal -->
    <div v-if="showPlayer" class="fixed inset-0 z-50 flex items-center justify-center bg-black bg-opacity-80">
      <div class="relative w-full max-w-4xl aspect-video">

        <!-- Loading Spinner -->
        <div v-if="isVideoLoading"
          class="absolute inset-0 z-50 flex items-center justify-center bg-black bg-opacity-60">
          <div class="loader"></div>
        </div>


        <iframe src="https://player.vimeo.com/video/1081429318?autoplay=1" class="w-full h-full rounded-lg"
          frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen
          @load="isVideoLoading = false" />


        <button @click="showPlayer = false"
          class="absolute top-2 right-2 bg-red-600 text-white rounded-full px-3 py-1 font-bold text-xl hover:bg-red-700 transition">
          ✕
        </button>
      </div>
    </div>

    <!-- Resume PDF Modal -->
    <div v-if="showResume" class="fixed inset-0 z-50 flex items-center justify-center bg-black bg-opacity-80 p-4">
      <div class="relative w-full max-w-5xl h-[80vh] bg-white rounded-lg overflow-hidden">
        <iframe src="/public/resume_2025.pdf" class="w-full h-full" frameborder="0"></iframe>
        <button @click="showResume = false"
          class="absolute top-2 right-2 bg-red-600 text-white rounded-full px-3 py-1 font-bold text-xl hover:bg-red-700 transition">
          ✕
        </button>
      </div>
    </div>
  </section>
</template>


<script>
export default {
  data() {
    return {
      showPlayer: false,
      showResume: false,
      isVideoLoading: false
    }
  },
  watch: {
    showPlayer(val) {
      if (val) {
        this.isVideoLoading = true
      }
    }
  }
}
</script>

<style scoped>
section {
  position: relative;
  overflow: hidden;
}

video {
  filter: brightness(0.6);
}

h1 span {
  text-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
}

button {
  box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
}

/* Spinner Styles */
.loader {
  border: 6px solid #f3f3f3;
  border-top: 6px solid #38bdf8;
  /* Sky blue */
  border-radius: 50%;
  width: 60px;
  height: 60px;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(360deg);
  }
}
</style>
