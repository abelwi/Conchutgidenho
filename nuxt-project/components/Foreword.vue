<template>
  <div
    class="fixed inset-0 z-20 flex flex-col transition-opacity duration-[1200ms] pointer-events-none"
    :class="[
      show ? 'opacity-100 pointer-events-auto' : 'opacity-0 pointer-events-none',
    ]"
    style="background-color: #F6CF81;"
  >
    <!-- Close button -->
    <button
      @click="$emit('close')"
      class="absolute top-6 right-8 text-2xl font-bold text-gray-600 hover:text-black transition duration-300"
    >
      ✕
    </button>

    <!-- Foreword content -->
    <div class="text-center p-10">
      <h2 class="text-5xl font-serif mb-6">Lời mở đầu</h2>
      <p class="text-lg font-mono italic">
        Đây là phần nội dung lời mở đầu của bạn. Xin chào! 🌿
      </p>
    </div>
  </div>
</template>

<script setup>
defineProps({ show: Boolean })
defineEmits(['close'])
</script>
