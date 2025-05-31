<template>
  <div class="fixed inset-0 z-20 bg-[#FFE8B9] flex flex-col items-center justify-center text-center">
    <button
      @click="$emit('close')"
      class="absolute top-6 right-8 text-2xl font-bold text-gray-600 hover:text-black transition"
    >
      ✕
    </button>
    <h2 class="text-5xl font-serif mb-6">Tôi thấy gì trên cuộc đời này</h2>
    <p class="text-lg font-mono italic">Những câu chuyện mà tôi sẽ kể cậu nghe</p>
  </div>
</template>

<script setup>
defineEmits(['close'])
</script>
