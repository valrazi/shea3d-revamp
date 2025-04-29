<template>
    <section 
        class="about" 
        id="about"
        ref="sectionRef"
        :class="{ 'fade-in': isVisible, 'fade-out': !isVisible }"
    >
        <div class="about__container">
            <div class="about__content">
                <div class="about__image-container">
                    <img 
                        src="../public/about_logo.jpg" 
                        alt="About Logo" 
                        class="about__image"
                    >
                </div>
                <div class="about__text-content">
                    <h1 class="text-4xl font-bold tracking-widest mb-8 text-white">ABOUT ME</h1>
                    <p class="about__description">
                        Hi, I'm Syahdan Micoy Nazera. I’m an FX Artist and also TD from Indonesia, 
                        passionate about crafting stunning visual effects for film TV, and commercials. 
                    </p>
                    <p class="about__text">
                        In addition to my FX expertise, I excel at technical problem-solving, 
                        developing tools and scripts to streamline workflows and optimize production pipelines. 
                        I work with Python and VEX, combining creativity with technical 
                        skills to deliver efficient and impactful solutions.
                    </p>
                    <div class="about__stats">
                        <div class="stat">
                            <span class="stat__number">3+</span>
                            <span class="stat__label">Years Experience</span>
                        </div>
                        <div class="stat">
                            <span class="stat__number">15+</span>
                            <span class="stat__label">Projects Completed</span>
                        </div>
                    </div>
                </div>
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
.about {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 4rem 2rem;
    background: linear-gradient(to bottom, black, transparent, black);
    color: #f5f5f5;
}

.about__container {
    max-width: 1200px;
    margin: 0 auto;
    width: 100%;
}

.about__content {
    display: flex;
    flex-direction: row;
    align-items: center;
    gap: 3rem;
}

.about__image-container {
    flex: 1;
    display: flex;
    justify-content: center;
}

.about__image {
    width: 300px;
    height: 300px;
    border-radius: 50%;
    box-shadow: 0 8px 15px rgba(0, 0, 0, 0.3);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.about__image:hover {
    transform: scale(1.05);
    box-shadow: 0 12px 20px rgba(0, 0, 0, 0.4);
}

.about__text-content {
    flex: 2;
    text-align: left;
}

.about__title {
    font-size: 4xl;
    font-weight: bold;
    letter-spacing: 0.05em;
    text-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
    margin-bottom: 1rem;
    text-transform: uppercase;
    color: white;
}

.about__description {
    font-size: 1.25rem;
    margin-bottom: 1.5rem;
    line-height: 1.8;
    font-weight: 300;
    color: rgba(255, 255, 255, 0.9);
}

.about__text {
    font-size: 1.1rem;
    line-height: 1.8;
    margin-bottom: 2rem;
    color: rgba(255, 255, 255, 0.8);
    font-weight: 300;
}

.about__stats {
    display: flex;
    gap: 4rem;
    margin-top: 2rem;
    border-top: 2px solid rgb(74, 222, 128);
    padding-top: 2rem;
}

.stat {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.5rem;
}

.stat__number {
    font-size: 2.5rem;
    font-weight: 500;
    color: rgb(74, 222, 128);
}

.stat__label {
    font-size: 1rem;
    color: rgba(255, 255, 255, 0.7);
    font-weight: 300;
    letter-spacing: 0.05em;
}

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

@media (max-width: 768px) {
    .about__content {
        flex-direction: column;
        text-align: center;
    }

    .about__image {
        width: 200px;
        height: 200px;
    }

    .about__title {
        font-size: 2.5rem;
    }

    .about__description {
        font-size: 1.25rem;
    }

    .about__stats {
        gap: 2rem;
    }

    .stat__number {
        font-size: 2rem;
    }
}
</style>