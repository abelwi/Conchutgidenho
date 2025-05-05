<template>
    <div v-if="show" class="fixed inset-0 bg-[#F6CF81] z-50 flex flex-col items-center justify-center p-10">
      <button @click="$emit('close')" class="absolute top-4 right-6 text-2xl">✖</button>
      <h2 class="text-4xl font-serif mb-6">Câu chuyện của tôi</h2>
      <p class="text-lg font-mono italic">
        Đây là một phần nội dung bạn có thể thêm cho câu chuyện.<br />
        Có thể kéo dài nhiều đoạn, hình ảnh hoặc hoạt cảnh ở đây.
      </p>
    </div>
  </template>
  
  <script setup>
  defineProps({
    show: Boolean
  })
  defineEmits(['close'])
  </script>
  