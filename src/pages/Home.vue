<template>
  <section
    class="max-w-4xl mx-auto flex md:flex-row flex-col justify-center items-center gap-8 h-screen mt-24 md:mt-0"
  >
    <img
      class="md:w-[300px] w-56 rounded-t-full border-4 border-[#7a685d] shadow-md"
      :src="kaye"
      alt=""
    />
    <div>
      <div class="flex flex-col p-2">
        <FontText addedClass="my-4 text-center" sizeVariant="xlbold">
          👋Hi! I'm Wyncylle Kaye!
        </FontText>
        <hr class="border-t-2 border-[#d49f7b]" />
      </div>
      <FontText addedClass="my-4 leading-relaxed text-center" sizeVariant="large">
        <span class="font-semibold"
          >An aspiring virual assistant passionate about helping businesses grow through creative
          and efficient solutions</span
        >
      </FontText>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import FontText from '@/components/FontText.vue'
import kaye from '/kayi.jpg'
// import kaye from '/flyers/1.png'
</script>
