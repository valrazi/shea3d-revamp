<template>
    <section class="min-h-screen bg-black text-white py-20" id="contact" ref="sectionRef" :class="{ 'fade-in': isVisible, 'fade-out': !isVisible }">
        <div class="max-w-6xl mx-auto px-4">
            <!-- Header -->
            <div class="text-center mb-16">
                <h2 class="text-5xl font-bold tracking-wider mb-8 text-white transform hover:scale-105 transition-transform duration-300">
                    GET IN TOUCH
                </h2>
                <div class="w-32 h-1 bg-gradient-to-r from-green-500 to-green-300 mx-auto mb-8 rounded-full"></div>
            </div>

            <!-- Contact Info -->
            <div class="max-w-2xl mx-auto">
                <div class="relative">
                    <div class="absolute inset-0 bg-gradient-to-br from-green-500/10 to-transparent rounded-3xl blur-3xl"></div>
                    <div class="relative bg-white/5 backdrop-blur-lg rounded-3xl p-8 border border-white/10 hover:border-green-500/50 transition-all duration-500">
                        <h3 class="text-2xl font-semibold mb-6 text-green-400">Contact Information</h3>
                        
                        <div class="space-y-6">
                            <div class="flex items-center space-x-4 group">
                                <div class="w-12 h-12 rounded-full bg-green-500/10 flex items-center justify-center group-hover:bg-green-500/20 transition-all duration-300">
                                    <font-awesome-icon :icon="['fas', 'envelope']" class="text-xl text-green-400" />
                                </div>
                                <div>
                                    <h4 class="text-sm text-gray-400">Email</h4>
                                    <a href="mailto:shea@3d-portfolio.com" class="text-white hover:text-green-400 transition-colors">shdnea@gmail.com</a>
                                </div>
                            </div>

                            <div class="flex items-center space-x-4 group">
                                <div class="w-12 h-12 rounded-full bg-green-500/10 flex items-center justify-center group-hover:bg-green-500/20 transition-all duration-300">
                                    <font-awesome-icon :icon="['fab', 'linkedin']" class="text-xl text-green-400" />
                                </div>
                                <div>
                                    <h4 class="text-sm text-gray-400">LinkedIn</h4>
                                    <a href="https://www.linkedin.com/in/snazera/" target="_blank" rel="noopener noreferrer" class="text-white hover:text-green-400 transition-colors">linkedin.com/in/snazera</a>
                                </div>
                            </div>

                            <div class="flex items-center space-x-4 group">
                                <div class="w-12 h-12 rounded-full bg-green-500/10 flex items-center justify-center group-hover:bg-green-500/20 transition-all duration-300">
                                    <font-awesome-icon :icon="['fab', 'instagram']" class="text-xl text-green-400" />
                                </div>
                                <div>
                                    <h4 class="text-sm text-gray-400">Instagram</h4>
                                    <a href="https://www.instagram.com/shdn_ea/" target="_blank" rel="noopener noreferrer" class="text-white hover:text-green-400 transition-colors">instagram.com/shdn_ea</a>
                                </div>
                            </div>

                            <div class="flex items-center space-x-4 group">
                                <div class="w-12 h-12 rounded-full bg-green-500/10 flex items-center justify-center group-hover:bg-green-500/20 transition-all duration-300">
                                    <font-awesome-icon :icon="['fab', 'vimeo']" class="text-xl text-green-400" />
                                </div>
                                <div>
                                    <h4 class="text-sm text-gray-400">Vimeo</h4>
                                    <a href="https://vimeo.com/user103541021" target="_blank" rel="noopener noreferrer" class="text-white hover:text-green-400 transition-colors">vimeo.com/user103541021</a>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Copyright Section -->
            <div class="mt-32 text-center">
                <div class="w-full border-t border-white/10"></div>
                <p class="mt-6 text-sm text-gray-400">
                    © {{ new Date().getFullYear() }} Syahdan Micoy Nazera and Respective Studios  •  All media are for showreel purposes only
                </p>
            </div>
        </div>
    </section>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';

const sectionRef = ref<HTMLElement | null>(null);
const isVisible = ref(false);

const observerOptions = {
    root: null,
    rootMargin: '0px',
    threshold: 0.1
};

let observer: IntersectionObserver;

onMounted(() => {
    observer = new IntersectionObserver(([entry]) => {
        isVisible.value = entry.isIntersecting;
    }, observerOptions);

    if (sectionRef.value) {
        observer.observe(sectionRef.value);
    }
});

onUnmounted(() => {
    if (observer) {
        observer.disconnect();
    }
});
</script>

<style scoped>
.fade-in {
    opacity: 1;
    transform: translateY(0);
    transition: opacity 0.8s ease-in-out, transform 0.8s ease-in-out;
}

.fade-out {
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.8s ease-in-out, transform 0.8s ease-in-out;
}
</style>