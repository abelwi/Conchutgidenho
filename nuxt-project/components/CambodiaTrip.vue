<template>
  <div class="fixed inset-0 z-20 bg-[#FFE8B9] flex flex-col items-center justify-center text-center">
    <button
      @click="$emit('close')"
      class="absolute top-6 right-8 text-2xl font-bold text-gray-600 hover:text-black transition"
    >
      ✕
    </button>
    <h2 class="text-5xl font-serif mb-6">Cambodia Trip</h2>
    <p class="text-lg font-mono italic">Hành trình khám phá đất nước Chùa Tháp 🛕</p>
  </div>
</template>

<script setup>
defineEmits(['close'])
</script>
