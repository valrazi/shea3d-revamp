<script setup lang="ts">
interface Project {
    id: number;
    title: string;
    description?: string;
    category?: string;
    platform: string;
    image: string;
    link?: string;
}

const projects: Project[] = [
    {
        id: 1,
        title: 'Moving',
        platform: 'Disney+',
        image: 'https://res.cloudinary.com/dj2fvefmt/image/upload/v1745939402/fj3kfzcsovbxu2mplqzh.jpg'
    },
    {
        id: 2,
        title: 'Nightmare & Daydreams',
        platform: 'Netflix',
        image: 'https://res.cloudinary.com/dj2fvefmt/image/upload/v1745939402/xrorgjelkm6hmuv43pco.jpg'
    },
    {
        id: 3,
        title: 'Muromachi Burai (室町無頼)',
        platform: 'Featured Film',
        image: 'https://res.cloudinary.com/dj2fvefmt/image/upload/v1745939401/xm9uzohurbjydrsy9gye.jpg'
    },
    {
        id: 4,
        title: 'Siksa Kubur',
        platform: 'Featured Film',
        image: 'https://res.cloudinary.com/dj2fvefmt/image/upload/v1745939401/fpvbdsidxq5rlkrlj8el.jpg'
    },
    {
        id: 5,
        title: 'Lembayung',
        platform: 'Featured Film',
        image: 'https://res.cloudinary.com/degml11da/image/upload/v1730103857/Lembayung_kyeraz.webp'
    },
    {
        id: 6,
        title: 'Kabut Berduri',
        platform: 'Netflix',
        image: 'https://res.cloudinary.com/degml11da/image/upload/v1730103857/KabutBerduri_he6lss.webp'
    },
    {
        id: 7,
        title: 'Sri Asih',
        platform: 'Featured Film',
        image: 'https://res.cloudinary.com/degml11da/image/upload/v1730103857/sriAsih_mknuut.jpg'
    },
    {
        id: 8,
        title: 'Tira and The Nine Dragon',
        platform: 'Disney+',
        image: 'https://res.cloudinary.com/degml11da/image/upload/v1730103857/tiraNineDragon_sxbbfj.jpg'
    },
    {
        id: 9,
        title: 'LEGO DREAMZzz Night of The Never Witch',
        platform: 'Netflix',
        image: 'https://res.cloudinary.com/dj2fvefmt/image/upload/v1745938116/qsziup3ri2h31ia3lnrs.webp'
    },
    {
        id: 10,
        title: 'The Siege at Thorn High',
        platform: 'Featured Film',
        image: 'https://res.cloudinary.com/dj2fvefmt/image/upload/v1745940506/auuzgfq0kwo34vsnrcgb.jpg'
    }
]

const selectedplatform = ref<string>('All')
const categories = ['All', ...new Set(projects.map(p => p.platform))]

const filteredProjects = computed(() => {
    if (selectedplatform.value === 'All') return projects
    return projects.filter(p => p.platform === selectedplatform.value)
})

const scrollContainer = ref<HTMLElement | null>(null)

// Add loading state management
const loadedImages = ref(new Set<number>())
const handleImageLoad = (projectId: number) => {
    loadedImages.value.add(projectId)
}

// Enhance scroll behavior with smooth animation
const scroll = (direction: 'left' | 'right') => {
    if (!scrollContainer.value) return
    const scrollAmount = Math.min(scrollContainer.value.clientWidth * 0.8, 800)
    const targetScroll = scrollContainer.value.scrollLeft + (direction === 'left' ? -scrollAmount : scrollAmount)
    scrollContainer.value.scrollTo({
        left: targetScroll,
        behavior: 'smooth'
    })
}
</script>

<template>
    <div class="w-full bg-black">
        <div class="w-full mx-auto px-4 py-16 max-w-[1920px]">
            <h2 class="text-5xl font-bold tracking-wider mb-8 text-center text-white transform hover:scale-105 transition-transform duration-300" 
                style="text-shadow: 0 4px 8px rgba(0, 0, 0, 0.4)">
                WORKS
            </h2>
            <div class="w-32 h-1 bg-gradient-to-r from-green-500 to-green-300 mx-auto mb-16 rounded-full"></div>
            
            <!-- Platform Filter -->
            <div class="flex flex-wrap justify-center gap-8 mb-16">
                <button 
                    v-for="platform in categories" 
                    :key="platform"
                    @click="selectedplatform = platform"
                    :class="[
                        'px-8 py-3 transition-all duration-300 text-base tracking-wide relative overflow-hidden',
                        selectedplatform === platform 
                            ? 'text-green-400 font-medium' 
                            : 'text-gray-400 hover:text-white'
                    ]"
                >
                    {{ platform }}
                    <div 
                        v-if="selectedplatform === platform"
                        class="absolute bottom-0 left-0 w-full h-0.5 bg-gradient-to-r from-green-500 to-green-300 
                               transform origin-left animate-[slideIn_0.3s_ease-out]"
                    ></div>
                </button>
            </div>

            <!-- Project Grid with Horizontal Scroll -->
            <div class="relative group">
                <!-- Gradient Fades -->
                <div class="absolute left-0 top-0 bottom-0 w-32 bg-gradient-to-r from-black to-transparent pointer-events-none z-10 
                            opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
                <div class="absolute right-0 top-0 bottom-0 w-32 bg-gradient-to-l from-black to-transparent pointer-events-none z-10 
                            opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>

                <!-- Scroll Buttons -->
                <button 
                    @click="scroll('left')"
                    class="absolute left-12 top-1/2 -translate-y-1/2 z-20 bg-black/90 text-white p-4 rounded-full 
                           opacity-0 group-hover:opacity-100 transition-all duration-300 hover:bg-green-500 
                           transform hover:scale-110 shadow-xl"
                >
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
                    </svg>
                </button>

                <button 
                    @click="scroll('right')"
                    class="absolute right-12 top-1/2 -translate-y-1/2 z-20 bg-black/90 text-white p-4 rounded-full 
                           opacity-0 group-hover:opacity-100 transition-all duration-300 hover:bg-green-500 
                           transform hover:scale-110 shadow-xl"
                >
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                    </svg>
                </button>

                <!-- Scrollable Container -->
                <div 
                    ref="scrollContainer"
                    class="flex overflow-x-auto scrollbar-hide gap-8 px-12 snap-x snap-mandatory"
                >
                    <div 
                        v-for="project in filteredProjects" 
                        :key="project.id" 
                        class="flex-none w-[300px] snap-start transform transition-all duration-500 hover:-translate-y-2"
                    >
                        <div class="relative overflow-hidden rounded-lg shadow-2xl mb-4 bg-gray-900">
                            <!-- Loading Placeholder -->
                            <div 
                                v-show="!loadedImages.has(project.id)"
                                class="absolute inset-0 bg-gray-800 animate-pulse"
                            ></div>
                            
                            <!-- Poster Image -->
                            <div class="aspect-[2/3] relative overflow-hidden cursor-pointer">
                                <img 
                                    :src="project.image" 
                                    :alt="project.title" 
                                    @load="handleImageLoad(project.id)"
                                    class="w-full h-full object-cover transition-all duration-700 
                                           hover:grayscale hover:scale-105 hover:brightness-75"
                                    :class="{'opacity-0': !loadedImages.has(project.id)}"
                                    loading="lazy"
                                >
                                <!-- Hover Overlay -->
                                <div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent 
                                            opacity-0 hover:opacity-100 transition-opacity duration-500
                                            flex items-end p-6">
                                    <div class="transform translate-y-4 hover:translate-y-0 transition-transform duration-300">
                                        <span class="text-green-400 text-sm font-medium mb-2 block">{{ project.platform }}</span>
                                        <h3 class="text-white text-xl font-bold">{{ project.title }}</h3>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.scrollbar-hide {
    -ms-overflow-style: none;
    scrollbar-width: none;
}
.scrollbar-hide::-webkit-scrollbar {
    display: none;
}

@keyframes slideIn {
    from { transform: scaleX(0); }
    to { transform: scaleX(1); }
}

@keyframes fadeIn {
    from { opacity: 0; transform: translateY(10px); }
    to { opacity: 1; transform: translateY(0); }
}

.project-enter-active {
    animation: fadeIn 0.5s ease-out;
}

/* Add smooth transition for image loading */
img {
    transition: opacity 0.3s ease-in-out;
}
</style>
