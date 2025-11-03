<template>
  <div class="max-w-6xl mx-auto px-4">
    <TitlePage> Portfolio </TitlePage>

    <div class="flex flex-col gap-10">
      <!-- Intro Section -->
      <!-- <section class="h-[40rem] bg-red-300 flex flex-col justify-center items-center">
        <div class="flex flex-col">
          <div class="flex gap-10 flex-wrap justify-center">
            <img
              class="w-[300px] rounded-t-full border-4 border-[#7a685d] shadow-md"
              :src="kaye"
              alt="Designer photo"
            />
            <div class="flex justify-center items-center max-w-xl">
              <FontText addedClass="leading-relaxed text-center" sizeVariant="large">
                <span class="font-semibold">
                  A passionate Canva designer and video editor who brings ideas to life through
                  creative visuals, smooth edits, and a touch of storytelling flair.
                </span>
              </FontText>
            </div>
          </div>
        </div>
      </section> -->

      <section v-for="(category, index) in portfolio" :key="index" class="flex flex-col gap-10">
        <FontText
          sizeVariant="xxlbold"
          addedClass="text-center text-[#0e221b] mt-10 uppercase tracking-widest"
        >
          {{ category.type.replace('-', ' ') }}
        </FontText>

        <div v-if="category.type === 'social-media'" class="space-y-12">
          <div
            v-for="(contentGroup, cIndex) in category.content"
            :key="cIndex"
            class="flex flex-col gap-6"
          >
            <div class="flex items-center justify-center">
              <FontText sizeVariant="largebold" addedClass="capitalize text-center text-[#7a685d] ">
                <div class="bg-[#7a685d] p-3 rounded-full text-white">
                  {{ contentGroup.type }}
                </div>
              </FontText>
            </div>

            <div
              class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-6 justify-items-center"
            >
              <div
                v-for="(item, iIndex) in contentGroup.content"
                :key="iIndex"
                class="w-full max-w-[200px]"
              >
                <img
                  :src="item.file"
                  alt="Portfolio item"
                  class="w-full h-auto rounded-xl shadow-lg hover:scale-105 transition-transform duration-300"
                />
              </div>
            </div>
          </div>
        </div>

        <div v-else-if="category.type === 'videos'" class="text-center text-gray-500 italic my-20">
          <FontText sizeVariant="mediumbold">Videos coming soon 🎥</FontText>
        </div>
      </section>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import FontText from '@/components/FontText.vue'
import TitlePage from '@/components/TitlePage.vue'
import kaye from '/kayi.jpg'

// ✅ Import your portfolio JSON (from /public/json/portfolio.json)
import portData from '../json/portfolio.json'

const portfolio = ref(portData)
</script>
