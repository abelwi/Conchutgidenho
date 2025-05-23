<template>
  <div class="h-screen flex flex-col overflow-hidden relative">
    <!-- Top section -->
    <div
      class="h-1/2 bg-[url(/images/my-avatar.jpg)] bg-cover bg-no-repeat bg-[20%_30%] cursor-pointer transition-transform duration-[1200ms] z-10"
      :class="{ '-translate-y-full': activePage !== null }"
      @click="openPage('foreword')"
    >
      <div class="w-2/5 h-full inline-flex flex-col items-center justify-center space-y-7">
        <h1 class="font-serif text-5xl"><strong>Còn chút gì để nhớ?</strong></h1>
        <p class="flex justify-center font-mono italic">
          Cuộc sống trong đôi mắt này <br />
          Có vui có buồn có cả mây bay
        </p>
      </div>
    </div>

    <!-- Bottom sections -->
    <div
      class="flex flex-col flex-1 transition-transform duration-700 z-10"
      :class="{ 'translate-y-full': activePage !== null }"
    >
      <div class="flex-1 bg-[#FFE8B9] flex items-center justify-center cursor-pointer" @click="openPage('cambodia')">
        <p class="text-3xl font-serif tracking-wide">Cambodia Trip</p>
      </div>
      <div class="flex-1 bg-[#F6CF81] flex items-center justify-center cursor-pointer" @click="openPage('life')">
        <p class="text-3xl font-serif tracking-wide">Tôi thấy gì trên cuộc đời này</p>
      </div>
      <div class="flex-1 bg-[#F7D99C] flex items-center justify-center cursor-pointer" @click="openPage('memory')">
        <p class="text-3xl font-serif tracking-wide">Còn chút gì để nhớ!?</p>
      </div>
    </div>

    <!-- Always mounted component, faded with opacity -->
    <div
      v-if="activeComponent"
      :class="[
        'fixed inset-0 z-20 transition-opacity duration-1000 pointer-events-none',
        showContent ? 'opacity-100 pointer-events-auto' : 'opacity-0',
      ]"
    >
      <component :is="activeComponent" @close="closePage" />
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'
import Foreword from '~/components/Foreword.vue'
import CambodiaTrip from '~/components/CambodiaTrip.vue'
import LifeView from '~/components/LifeView.vue'
import Memory from '~/components/Memory.vue'

const activePage = ref(null)
const activeComponent = ref(null)
const showContent = ref(false)

const openPage = (page) => {
  activePage.value = page
  showContent.value = false

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

  // Fade in content after small delay (during slide animation)
  setTimeout(() => {
    showContent.value = true
  }, 200) // starts fade ~200ms after transition begins
}

const closePage = () => {
  showContent.value = false
  // Wait for fade out before resetting
  setTimeout(() => {
    activePage.value = null
    activeComponent.value = null
  }, 500)
}
</script>
