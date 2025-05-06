<template>
  <!-- Full screen wrapper -->
  <div class="h-screen flex flex-col overflow-hidden relative ">

    <!-- Top section (1/2 height) -->
    <div
      class="h-1/2 bg-[url(/images/my-avatar.jpg)] bg-cover bg-no-repeat bg-[20%_30%] cursor-pointer transition-transform duration-[1200ms] z-10"
      :class="{ '-translate-y-full': showStory }"
      @click="showStory = true"
    >
      <div class="w-2/5 h-full inline-flex flex-col items-center justify-center space-y-7">
        <h1 class="font-serif text-5xl"><strong>Còn chút gì để nhớ?</strong></h1>
        <p class="flex justify-center font-mono italic">
          Cuộc sống trong đôi mắt này <br />
          Có vui có buồn có cả mây bay
        </p>
      </div>
    </div>

    <!-- Bottom section (3x 1/6 = 1/2 height) -->
    <div
      class="flex flex-col flex-1 transition-transform duration-700 z-10"
      :class="{ 'translate-y-full': showStory }"
    >
      <div class="flex-1 bg-[#FFE8B9] flex items-center justify-center">
        <p class="text-3xl font-serif tracking-wide">Cambodia Trip</p>
      </div>
      <div class="flex-1 bg-[#F6CF81] flex items-center justify-center">
        <p class="text-3xl font-serif tracking-wide">Tôi thấy gì trên cuộc đời này</p>
      </div>
      <div class="flex-1 bg-[#F7D99C] flex items-center justify-center">
        <p class="text-3xl font-serif tracking-wide">Còn chút gì để nhớ!?</p>
      </div>
    </div>

    <!-- Showing Foreword -->
    <Foreword :show="showStory" @close="showStory = false" />
  
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Foreword from '~/components/Foreword.vue'

const showStory = ref(false)
</script>
