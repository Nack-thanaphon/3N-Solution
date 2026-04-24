<template>
  <section id="slider" class="relative w-full h-screen overflow-hidden bg-gray-900">
    <div class="relative h-full">
      <transition 
        :name="transitionName"
        @before-enter="beforeEnter"
        @after-enter="afterEnter"
      >
        <div 
          v-if="currentSlide"
          :key="currentSlide.id"
          class="absolute inset-0 flex items-center justify-center"
        >
          <img 
            :src="currentSlide.image" 
            :alt="currentSlide.alt"
            class="w-full h-full object-cover"
          />
          <div class="absolute inset-0 bg-gradient-to-t from-black/70 via-black/20 to-transparent"></div>
          <div class="absolute bottom-0 left-0 right-0 p-8 md:p-16">
            <div class="max-w-4xl mx-auto text-center text-white">
              <h2 class="text-3xl md:text-5xl font-bold mb-4">{{ currentSlide.title }}</h2>
              <p class="text-lg md:text-xl opacity-90">{{ currentSlide.description }}</p>
            </div>
          </div>
        </div>
      </transition>

      <button 
        @click="prevSlide"
        class="absolute left-4 top-1/2 -translate-y-1/2 z-20 p-3 rounded-full bg-white/20 hover:bg-white/40 backdrop-blur-sm transition-all text-white"
      >
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
        </svg>
      </button>

      <button 
        @click="nextSlide"
        class="absolute right-4 top-1/2 -translate-y-1/2 z-20 p-3 rounded-full bg-white/20 hover:bg-white/40 backdrop-blur-sm transition-all text-white"
      >
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
        </svg>
      </button>

      <div class="absolute bottom-8 left-1/2 -translate-x-1/2 z-20 flex gap-2">
        <button
          v-for="(slide, index) in slides"
          :key="slide.id"
          @click="goToSlide(index)"
          class="w-3 h-3 rounded-full transition-all"
          :class="index === currentIndex ? 'bg-white w-8' : 'bg-white/50 hover:bg-white/80'"
        ></button>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, computed, onMounted, onUnmounted } from 'vue'

const props = defineProps<{
  slides: Array<{
    id: string
    image: string
    alt: string
    title: string
    description: string
  }>
}>()

const currentIndex = ref(0)
const transitionName = ref<'slide-left' | 'slide-right'>('slide-left')
let autoplayInterval: ReturnType<typeof setInterval> | null = null

const currentSlide = computed(() => props.slides[currentIndex.value])

const nextSlide = () => {
  transitionName.value = 'slide-left'
  currentIndex.value = (currentIndex.value + 1) % props.slides.length
}

const prevSlide = () => {
  transitionName.value = 'slide-right'
  currentIndex.value = (currentIndex.value - 1 + props.slides.length) % props.slides.length
}

const goToSlide = (index: number) => {
  if (index > currentIndex.value) {
    transitionName.value = 'slide-left'
  } else {
    transitionName.value = 'slide-right'
  }
  currentIndex.value = index
}

const startAutoplay = () => {
  autoplayInterval = setInterval(nextSlide, 5000)
}

const stopAutoplay = () => {
  if (autoplayInterval) {
    clearInterval(autoplayInterval)
    autoplayInterval = null
  }
}

const beforeEnter = () => {
  stopAutoplay()
}

const afterEnter = () => {
  startAutoplay()
}

onMounted(() => {
  startAutoplay()
})

onUnmounted(() => {
  stopAutoplay()
})
</script>

<style scoped>
.slide-left-enter-active,
.slide-left-leave-active,
.slide-right-enter-active,
.slide-right-leave-active {
  transition: all 0.5s ease;
}

.slide-left-enter-from {
  transform: translateX(100%);
  opacity: 0;
}

.slide-left-leave-to {
  transform: translateX(-100%);
  opacity: 0;
}

.slide-right-enter-from {
  transform: translateX(-100%);
  opacity: 0;
}

.slide-right-leave-to {
  transform: translateX(100%);
  opacity: 0;
}
</style>
