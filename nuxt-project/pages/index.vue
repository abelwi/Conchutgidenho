<template>
  <div class="h-screen">
    <div class="bg-[url(/images/my-avatar.jpg)] bg-cover bg-no-repeat bg-[20%_30%] h-1/2 cursor-pointer"
    @click="showStory = true"
    >
      <div class="w-2/5 h-full inline-flex flex-col items-center justify-center space-y-7">
        <h1 class="font-serif text-5xl"><strong>Còn chút gì để nhớ?</strong></h1>
        <p class="flex justify-center font-mono italic">Cuộc sống trong đôi mắt này <br>
          Có vui có buồn có cả mây bay
        </p>
      </div>
    </div>

    <div class= "h-1/6 bg-[#FFE8B9]">
      <p class="w-1/4 h-full flex items-center justify-center text-3xl font-serif tracking-wide">Cambodia Trip</p>
    </div>
    <div class="h-1/6 bg-[#F6CF81]">
      <p class="w-1/3 h-full pl-14 flex items-center justify-center font-serif text-3xl tracking-wide">Tôi thấy gì trên cuộc đời này</p>
    </div>
    <div class="h-1/6 bg-[#F7D99C] ">
      <p class=" w-1/4 h-full pl-16 flex items-center justify-center font-serif text-3xl tracking-wide">Còn chút gì để nhớ!?</p>
    </div>
  </div>

  <ForeWord :show="showStory" @close="showStory = false" />
  </template>

<script setup>
import { ref } from 'vue'
import ForeWord from '~/components/ForeWord.vue'

const showStory = ref(false)
</script>

  