<template>
  <div class="h-screen flex flex-col overflow-hidden relative">

    <!-- Content always rendered behind -->
    <div class="absolute inset-0 z-0">
      <component :is="activeComponent" v-if="activeComponent" />
    </div>

    <!-- Top Curtain (slide up) -->
    <div
      class="h-1/2 bg-[url(/images/my-avatar.jpg)] bg-cover bg-no-repeat bg-[20%_30%] cursor-pointer transition-transform duration-[1200ms] z-10"
      :class="{ '-translate-y-full': isCurtainOpen }"
      @click="openCurtain('foreword')"
    >
      <div class="w-2/5 h-full inline-flex flex-col items-center justify-center space-y-7">
        <h1 class="font-serif text-5xl"><strong>Còn chút gì để nhớ?</strong></h1>
        <p class="flex justify-center font-mono italic">
          Cuộc sống trong đôi mắt này <br />
          Có vui có buồn có cả mây bay
        </p>
      </div>
    </div>

    <!-- Bottom Curtain (slide down) -->
    <div
      class="flex flex-col flex-1 transition-transform duration-[1200ms] z-10"
      :class="{ 'translate-y-full': isCurtainOpen }"
    >
      <div class="flex-1 bg-[#f8dda6] flex items-center justify-center cursor-pointer" @click="openCurtain('cambodia')">
        <p class="text-3xl font-serif tracking-wide">Cambodia Trip</p>
      </div>
      <div class="flex-1 bg-[#F6CF81] flex items-center justify-center cursor-pointer" @click="openCurtain('life')">
        <p class="text-3xl font-serif tracking-wide">Tôi thấy gì trên cuộc đời này</p>
      </div>
      <div class="flex-1 bg-[#F7D99C] flex items-center justify-center cursor-pointer" @click="openCurtain('memory')">
        <p class="text-3xl font-serif tracking-wide">Còn chút gì để nhớ!?</p>
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
import { ref } from 'vue'
import Foreword from '~/components/Foreword.vue'
import CambodiaTrip from '~/components/CambodiaTrip.vue'
import LifeView from '~/components/LifeView.vue'
import Memory from '~/components/Memory.vue'

const isCurtainOpen = ref(false)
const activeComponent = ref(null)

function openCurtain(page) {
  // Set content behind the curtain immediately
  switch (page) {
    case 'foreword':
      activeComponent.value = Foreword
      break
    case 'cambodia':
      activeComponent.value = CambodiaTrip
      break
    case 'life':
      activeComponent.value = LifeView
      break
    case 'memory':
      activeComponent.value = Memory
      break
  }

  // Open curtain right after
  isCurtainOpen.value = true
}

function closeCurtain() {
  // Close the curtain
  isCurtainOpen.value = false

  // After curtain closes (match animation duration), remove content
  setTimeout(() => {
    activeComponent.value = null
  }, 1200) // matches transition duration
}
</script>
