<template>
  <div class="h-screen flex flex-col items-center justify-center text-center bg-[#FFE8B9] relative px-6">
    <h2 class="text-5xl font-serif mb-6">Còn chút gì để nhớ</h2>
    <p class="text-lg font-mono italic">Nếu được quay về tuổi thơ thì sao?</p>
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
