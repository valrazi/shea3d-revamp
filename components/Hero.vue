<template>
    
    <section class="relative h-screen overflow-hidden">
        <video autoplay muted loop class="absolute inset-0 w-full h-full object-cover">
            <source src="../static/video/ocean.mp4" type="video/mp4">
            Your browser does not support the video tag.
        </video>
        <div class="absolute inset-0 flex flex-col items-center justify-center text-white gap-y-4">
            <h1 class="text-4xl font-bold text-center">SYAHDAN NAZERA</h1>
            <div class="flex flex-row gap-4">
                <button class="px-3 border border-white uppercase">Showreel</button>
                <button class="px-3 border border-white uppercase">Portfolio</button>
            </div>
        </div>
    </section>
</template>