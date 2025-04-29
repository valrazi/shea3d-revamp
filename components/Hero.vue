<template>
    <section class="relative w-full h-screen flex justify-center bg-black text-white overflow-hidden">
        <div class="absolute inset-0">
            <video autoplay loop muted playsinline controlslist="nodownload" disablePictureInPicture oncontextmenu="return false" class="w-full h-full object-cover">
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
                <button class="px-8 py-3 bg-green-400 text-black font-medium rounded-lg hover:bg-green-500 transition-colors">
                    Demoreel
                </button>
            </div>
        </div>
    </section>
</template>

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
</style>