<template>
    <nav class="fixed top-0 left-0 right-0 px-8 py-6 text-white z-[999]">
        <ul class="flex items-center justify-end gap-8 text-sm font-light">
            <li>
                <a href="#" @click.prevent="scrollToTop" class="font-medium uppercase tracking-wider hover:text-green-500 transition-colors duration-300">
                    Home
                </a>
            </li>
            <li>
                <a href="#about" @click.prevent="scrollToSection('about')" class="font-medium uppercase tracking-wider hover:text-green-500 transition-colors duration-300">
                    About
                </a>
            </li>
            <li>
                <a href="#works" @click.prevent="scrollToSection('works')" class="font-medium uppercase tracking-wider hover:text-green-500 transition-colors duration-300">
                    WORKS
                </a>
            </li>
            <li>
                <a href="#contact" @click.prevent="scrollToSection('contact')" class="font-medium uppercase tracking-wider hover:text-green-500 transition-colors duration-300">
                    Contact
                </a>
            </li>
        </ul>
    </nav>
</template>

<script setup>
const scrollToTop = () => {
    window.scrollTo({ top: 0, behavior: 'smooth' });
};

const scrollToSection = (sectionId) => {
    const element = document.getElementById(sectionId);
    if (element) {
        element.scrollIntoView({ behavior: 'smooth' });
    }
};
</script>

<style scoped>
nav {
    background: rgba(0, 0, 0, 0);
    backdrop-filter: blur(2px);
    transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
}
</style>
