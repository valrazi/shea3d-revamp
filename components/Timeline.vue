<template>
  <div class="timeline-container" ref="sectionRef" :class="{ 'fade-in': isVisible, 'fade-out': !isVisible }">
    <div class="timeline-header">
      <h2 class="text-4xl font-bold tracking-widest mb-8 text-center text-white">EXPERIENCES</h2>
      <div class="w-24 h-1 bg-green-400 mx-auto mb-8"></div>
    </div>
    <div class="timeline-wrapper">
      <div class="timeline-line"></div>
      <div v-for="(item, index) in timelineList" :key="index" class="timeline-item"
        :class="{ 'right': index % 2 === 0 }">
        <div class="timeline-content">
          <div class="timeline-dot"></div>
          <h3 class="time">{{ item.time }}</h3>
          <div class="corporate-info">
            <h4>{{ item.corporate.name }}</h4>
            <p class="location">{{ item.corporate.location }}</p>
          </div>
          <h5 class="role">{{ item.role }}</h5>
          <ul class="projects">
            <li v-for="(project, pIndex) in item.projects" :key="pIndex">
              {{ project }}
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';

const timelineList = [
  {
    time: '2022 - Present',
    corporate: {
      name: 'LMN FX',
      location: 'Jakarta, Indonesia'
    },
    role: 'FX TD',
    projects: [
      'The Siege at Thorn High',
      'Muromachi Burai (室町無頼)',
      'Kabut Berduri',
      'Nightmare & Daydreams',
      'LEMBAYUNG', 'Siksa Kubur',
      'LEGO DREAMZzz Night of The Never Witch',
      'Moving',
      'SAMAR'
    ]
  },

  {
    time: '2021 - 2022',
    corporate: {
      name: 'Lumine Studio',
      location: 'Jakarta, Indonesia'
    },
    role: 'Junior FX Artist',
    projects: [
      'Little Angel : Nursery Rhymes & Kids Songs',
      'Johny Walker Blue Label 3D Videotron Ads',
      'CIMB NIAGA 3D Videotron Ads',
      'Mary',
      'Sri Asih',
      'Tira And The Nine Dragon',
      'Moving (무빙)']
  },

  {
    time: '2018 - 2020 ',
    corporate: {
      name: 'RUS ANIMATION STUDIO',
      location: 'Kudus, Jawa Tengah'
    },
    role: 'Intern FX Artist ',
    projects: [
      'Petualangan Olla Ello',
      'GooGoo Space Journey',
      'Sabda Alam',
      'Internal VR Project']
  },

]

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
.timeline-container {
  padding: 2rem 0;
  width: 100%;
  position: relative;
}

.timeline-header {
  text-align: center;
  margin-bottom: 2rem;
}

.timeline-header h2 {
  text-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
}

.timeline-wrapper {
  position: relative;
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem 0;
}

.timeline-line {
  position: absolute;
  left: 50%;
  width: 2px;
  height: 100%;
  background: linear-gradient(180deg,
      rgba(0, 0, 0, 0) 0%,
      rgba(74, 222, 128, 1) 15%,
      rgba(74, 222, 128, 1) 85%,
      rgba(0, 0, 0, 0) 100%);
  transform: translateX(-50%);
}

.timeline-item {
  width: 50%;
  padding: 2rem;
  position: relative;
  opacity: 0;
  animation: fadeIn 0.5s ease-in-out forwards;
}

.timeline-item.right {
  margin-left: 50%;
}

.timeline-content {
  position: relative;
  padding: 1.5rem;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 15px;
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
  transition: transform 0.3s ease;
}

.timeline-content:hover {
  transform: translateY(-5px);
}

.timeline-dot {
  position: absolute;
  width: 20px;
  height: 20px;
  background: rgb(74, 222, 128);
  border-radius: 50%;
  top: 50%;
  border: 4px solid rgb(30, 27, 75);
}

.right .timeline-dot {
  left: -60px;
}

.timeline-item:not(.right) .timeline-dot {
  right: -60px;
}

.time {
  font-size: 1.25rem;
  font-weight: 300;
  color: rgb(74, 222, 128);
  margin-bottom: 0.5rem;
  letter-spacing: 0.05em;
}

.corporate-info h4 {
  font-size: 1.1rem;
  font-weight: 700;
  letter-spacing: 0.05em;
  margin-bottom: 0.25rem;
  color: rgb(255, 255, 255);
}

.location {
  font-size: 0.9rem;
  color: rgba(255, 255, 255, 0.7);
  margin-bottom: 0.5rem;
  font-weight: 300;
}

.role {
  font-size: 1rem;
  color: rgb(74, 222, 128);
  margin-bottom: 1rem;
  font-weight: 400;
  letter-spacing: 0.05em;
}

.projects {
  list-style: none;
  padding: 0;
}

.projects li {
  font-size: 0.9rem;
  color: rgba(255, 255, 255, 0.8);
  margin-bottom: 0.25rem;
  padding-left: 1rem;
  position: relative;
}

.projects li::before {
  content: "•";
  position: absolute;
  left: 0;
  color: rgb(74, 222, 128);
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

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@media (max-width: 768px) {
  .timeline-line {
    left: 2rem;
  }

  .timeline-item {
    width: 100%;
    margin-left: 0 !important;
    padding-left: 4rem;
  }

  .timeline-dot {
    left: -10px !important;
  }
}
</style>