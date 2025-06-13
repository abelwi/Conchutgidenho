<template>
  <div class="h-screen flex flex-col items-center justify-center text-center bg-[#FFE8B9] relative px-6">
    <h2 class="text-5xl font-serif mb-6">Tôi thấy gì trên cuộc đời này</h2>
    <p class="text-lg font-mono italic">Những câu chuyện mà tôi sẽ kể cậu nghe</p>

    <!-- Optional close button if needed -->
    <button
      @click="$emit('close')"
      class="fixed top-6 right-8 text-2xl font-bold text-gray-600 hover:text-black transition"
    >
      ✕
    </button>
  </div>
</template>

<script setup>
defineEmits(['close']) // Optional, can remove if not using close logic
</script>
