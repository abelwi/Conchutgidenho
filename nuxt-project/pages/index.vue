<template>
  <div class="h-screen flex flex-col overflow-hidden relative">
    <!-- Content always rendered behind -->
    <div class="absolute inset-0 z-0">
      <component :is="activeComponent" v-if="activeComponent" />
    </div>

    <!-- Top Curtain (image div + clicked topic + topics above it) -->
    <div
      class="transition-transform duration-[1200ms] z-10 flex flex-col"
      :style="{ height: topCurtainHeight }"
      :class="{ '-translate-y-full': isCurtainOpen }"
    >
      <!-- Image Div (always included) -->
      <div
        class="bg-[url(/images/my-avatar.jpg)] bg-cover bg-no-repeat bg-[20%_30%] cursor-pointer"
        :style="{ height: imageHeight }"
        @click="openCurtain('foreword')"
      >
        <div class="w-2/5 h-full inline-flex flex-col items-center justify-center space-y-7">
          <h1 class="font-serif text-5xl"><strong>Còn chút gì để nhớ?</strong></h1>
          <p class="flex justify-center font-mono italic">
            Cuộc sống trong đôi mắt này <br />
            Có vui có buồn có cả mây bay
          </p>
          <button class="btn bg-[#f2d08d]">Xem thêm</button>
        </div>
      </div>

      <!-- Topics above and including the clicked topic -->
      <div
        v-for="topic in topCurtainTopics"
        :key="topic.id"
        class="flex items-center justify-start cursor-pointer transition duration-300 hover:brightness-95 hover:scale-[1.04]"
        :style="{ height: topicHeight }"
        :class="topic.bgColor"
        @click="openCurtain(topic.id)"
      >
        <p class="text-3xl font-serif tracking-wide pl-28">{{ topic.title }}</p>
      </div>
    </div>

    <!-- Bottom Curtain (topics below the clicked topic) -->
    <div
      v-if="remainingTopics.length > 0"
      class="flex flex-col transition-transform duration-[1200ms] z-10"
      :style="{ height: bottomCurtainHeight }"
      :class="{ 'translate-y-full': isCurtainOpen }"
    >
      <div
        v-for="topic in remainingTopics"
        :key="topic.id"
        class="flex items-center justify-start cursor-pointer transition duration-300 hover:scale-[1.04]"
        :style="{ height: topicHeight }"
        :class="topic.bgColor"
        @click="openCurtain(topic.id)"
      >
        <p class="text-3xl font-serif tracking-wide pl-28">{{ topic.title }}</p>
      </div>
    </div>

    <!-- Close button, only when curtain is open -->
    <button
      v-if="isCurtainOpen"
      @click="closeCurtain"
      class="absolute top-6 right-8 z-0 text-2xl font-bold text-gray-600 hover:text-black transition"
    >
      ✕
    </button>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import Foreword from '~/pages/contents/Foreword.vue'
import CambodiaTrip from '~/pages/contents/CambodiaTrip.vue'
import LifeView from '~/pages/contents/LifeView.vue'
import Memory from '~/pages/contents/Memory.vue'

// Define topics (excluding the image div, which is handled separately)
const topics = [
  {
    id: 'cambodia',
    title: 'Cambodia Trip',
    component: CambodiaTrip,
    bgColor: 'bg-[#f8dda6]',
  },
  {
    id: 'life',
    title: 'Tôi thấy gì trên cuộc đời này',
    component: LifeView,
    bgColor: 'bg-[#F6CF81]',
  },
  {
    id: 'memory',
    title: 'Còn chút gì để nhớ!?',
    component: Memory,
    bgColor: 'bg-[#F7D99C]',
  },
]

const isCurtainOpen = ref(false)
const selectedTopicId = ref(null)
const activeComponent = ref(null)

// Compute topics for the top curtain (clicked topic + topics above it)
const topCurtainTopics = computed(() => {
  if (!selectedTopicId.value || selectedTopicId.value === 'foreword') return []
  const selectedIndex = topics.findIndex((topic) => topic.id === selectedTopicId.value)
  return topics.slice(0, selectedIndex + 1)
})

// Compute remaining topics (topics below the clicked topic)
const remainingTopics = computed(() => {
  if (!selectedTopicId.value || selectedTopicId.value === 'foreword') return topics
  const selectedIndex = topics.findIndex((topic) => topic.id === selectedTopicId.value)
  return topics.slice(selectedIndex + 1)
})

// Calculate dynamic heights
const imageHeight = computed(() => '50vh') // Image div is always 1/2 of the screen height
const topicHeight = computed(() => '16.67vh') // Each topic takes 1/6 of screen height (100/6)

const topCurtainHeight = computed(() => {
  const baseHeight = 50 // Image div height in vh
  const additionalHeight = topCurtainTopics.value.length * (100 / 6) // Add 1/6 for each topic
  return `${baseHeight + additionalHeight}vh`
})

const bottomCurtainHeight = computed(() => {
  const remainingHeight = remainingTopics.value.length * (100 / 6) // 1/6 for each remaining topic
  return `${remainingHeight}vh`
})

function openCurtain(topicId) {
  selectedTopicId.value = topicId
  if (topicId === 'foreword') {
    activeComponent.value = Foreword
  } else {
    const topic = topics.find((t) => t.id === topicId)
    if (topic) {
      activeComponent.value = topic.component
    }
  }
  isCurtainOpen.value = true
}

function closeCurtain() {
  isCurtainOpen.value = false
  setTimeout(() => {
    activeComponent.value = null
    selectedTopicId.value = null
  }, 1200)
}

selectedTopicId.value = 'foreword'
</script>