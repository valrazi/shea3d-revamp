<template>
    <section class="w-full min-h-svh bg-black flex flex-col items-center justify-center">
        <div class="w-[60%] h-[60%] rounded-xl flex flex-col gap-4 p-4  items-center justify-evenly  bg-gray-800 ">
            <img src="../public/logo.jpeg" class="w-32 mt-8 rounded-full" alt="">
            <p class="text-center text-xs text-gray-300 lg:w-1/2 lg:text-sm">I am FX TD from Indonesia, specialized in Pyro
                Simulation, FLIP, and Vellum. Besides that I also master several programming languages
                such as VEX, Python, and a bit of C++ Thanks for checking out my reel!</p>

            <div class="flex flex-row gap-2 text-white text-xl">
                <font-awesome-icon :icon="['fab', 'youtube']" />
                <font-awesome-icon :icon="['fab', 'linkedin']" />
                <font-awesome-icon :icon="['fab', 'vimeo']" />
                <font-awesome-icon :icon="['fab', 'instagram']" />
                <font-awesome-icon :icon="['fab', 'twitter']" />
            </div>
        </div>
    </section>
</template>