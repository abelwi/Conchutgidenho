<template>
  <div ref="scrollContainer" class="flex flex-col h-full overflow-y-scroll snap-y snap-mandatory bg-[#FFE8B9]">
    <!-- Optional: Table of Contents (first screen) -->
    <div class="snap-start flex justify-between px-10 space-x-4">
      <div class="w-1/3 pt-10 space-y-10">
        <h2 class="text-4xl font-serif mb-8">Cambodia Trip</h2>
        <ul class="font-mono underline space-y-14">
          <li
            v-for="section in sectionOrder"
            :key="section.id"
            class="cursor-pointer hover:text-blue-700"
            @click="scrollTo(section.id)"
          >
            {{ section.title }}
          </li>
        </ul>
      </div>
       <!-- Full image section (optional) -->
      <section class="snap-start min-h-screen flex items-center justify-center w-2/3">
        <img src="/public/images/14C61CD2-B829-47CD-909C-BD43A3B123C2.JPG" alt="Cambodia avatar" class="max-w-full max-h-screen rounded-lg shadow-lg object-contain" />
      </section>
    </div>

    <!-- Content sections -->
    <section
      v-for="section in sectionOrder"
      :key="section.id"
      :ref="el => sectionRefs[section.id] = el"
      class="snap-start flex-shrink-0 flex flex-col mx-10"
    >
      <div class="mx-auto prose prose-lg">
        <component :is="section.component" />
      </div>
    </section>

    <!-- Close button -->
    <button
      @click="$emit('close')"
      class="fixed top-6 right-8 text-2xl font-bold text-gray-600 hover:text-black transition"
    >
      ✕
    </button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

defineEmits(['close'])

// Section imports
import SideStory from './CambodiaTrip/SideStory.vue'
import Part1 from './CambodiaTrip/Part1.vue'
import Part2 from './CambodiaTrip/Part2.vue'
import Part3 from './CambodiaTrip/Part3.vue'
import Part4 from './CambodiaTrip/Part4.vue'
import Part5 from './CambodiaTrip/Part5.vue'
import LastPart from './CambodiaTrip/LastPart.vue'

const sectionOrder = [
  { id: 'side', title: 'Phần ngoại chuyện', component: SideStory },
  { id: 'part1', title: 'Phần 1: Lần đầu được ra nước ngoài.', component: Part1 },
  { id: 'part2', title: 'Phần 2: Làng Chiphat', component: Part2 },
  { id: 'part3', title: 'Phần 3: Cambodian people don’t like Vietnamese people.', component: Part3 },
  { id: 'part4', title: 'Phần 4: Mình thèm được ngắm biển...', component: Part4 },
  { id: 'part5', title: 'Phần 5: Mình nhớ nhà rồi :(', component: Part5 },
  { id: 'last', title: 'Phần cuối: Những tiếc nuối còn sót lại...', component: LastPart },
]

const sectionRefs = ref({})
function scrollTo(id) {
  const el = sectionRefs.value[id]
  if (el) {
    el.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>
