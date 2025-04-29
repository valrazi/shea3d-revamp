<template>
    <nav class="fixed top-0 left-0 right-0 px-8 py-6 text-white z-[999]">
        <ul class="flex items-center justify-end gap-8 text-sm font-light">
            <li>
                <NuxtLink to="/about" class="font-medium uppercase tracking-wider hover:text-green-500 transition-colors duration-300">
                    About
                </NuxtLink>
            </li>
            <li>
                <NuxtLink to="/projects" class="font-medium uppercase tracking-wider hover:text-green-500 transition-colors duration-300">
                    WORKS
                </NuxtLink>
            </li>
            <li>
                <NuxtLink to="/contact" class="font-medium uppercase tracking-wider hover:text-green-500 transition-colors duration-300">
                    Contact
                </NuxtLink>
            </li>
        </ul>
    </nav>
</template>

<style scoped>
nav {
    background: rgba(0, 0, 0, 0);
    backdrop-filter: blur(2px);
    transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
}
</style>
