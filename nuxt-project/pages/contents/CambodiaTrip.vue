<template>
  <div class="h-screen flex justify-between bg-[#FFE8B9] relative px-5 py-5">
    <div class="w-1/2 space-y-14 pl-32">
      <h2 class="text-5xl font-serif">Cambodia Trip</h2>
      <p class="text-lg font-mono italic">Mục lục</p>
      <p>Phần ngoại chuyện: "Chút kinh nghiệm cho cậu nè!"</p>
      <p>Phần 1: Lần đầu được ra nước ngoài.</p>
      <p>Phần 2: Làng Chiphat</p>
      <p>Phần 3: Cambodian people don't like Vietnamese people.</p>
      <p>Phần 4: Mình thèm được ngắm biển...Thật là vui!</p>
      <p>Phần 5: Mình nhớ nhà rồii :((</p>
      <p>Phần cuối: Những tiếc nuối còn sót lại...</p>
    </div>
    <div class="w-1/2 py-16">
      <img src="/public/images/IMG_0502.jpg" alt="Cambodia avatar" class="w-full h-full mt-6 rounded-lg shadow-lg" />
    </div>
    <button
      @click="$emit('close')"
      class="fixed top-6 right-8 text-2xl font-bold text-gray-600 hover:text-black transition"
    >
      ✕
    </button>
  </div>
</template>

<script setup>
defineEmits(['close'])
</script>
