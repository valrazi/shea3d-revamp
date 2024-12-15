<script setup lang="ts">
const projects = [
    'https://res.cloudinary.com/degml11da/image/upload/v1730103856/Moving_qpf2ea.jpg',
    'https://res.cloudinary.com/degml11da/image/upload/v1730103856/NightmareAndDaydreams_aup497.jpg',
    'https://res.cloudinary.com/degml11da/image/upload/v1730103856/MMB_jzf3py.webp',
    'https://res.cloudinary.com/degml11da/image/upload/v1730103857/SiksaKubur_pdi3vg.jpg',
    'https://res.cloudinary.com/degml11da/image/upload/v1730103857/Lembayung_kyeraz.webp',
    'https://res.cloudinary.com/degml11da/image/upload/v1730103857/KabutBerduri_he6lss.webp',
    'https://res.cloudinary.com/degml11da/image/upload/v1730103857/sriAsih_mknuut.jpg',
    'https://res.cloudinary.com/degml11da/image/upload/v1730103857/tiraNineDragon_sxbbfj.jpg',
    'https://res.cloudinary.com/degml11da/image/upload/v1730103858/sabdaAlam_v2yqpo.jpg'
]

</script>
<template>
    <div class="w-full min-h-svh p-4 bg-black">
        <h1 class="text-white text-center text-2xl uppercase font-bold">Projects</h1>
        <div class="w-full min-h-svh p-4 flex flex-col gap-4 justify-center items-center bg-black lg:flex-row lg:flex-wrap">
            <img :src="img" alt="" class="min-w-[200px] max-h-[200px]" v-for="img in projects">
        </div>
    </div>
</template>