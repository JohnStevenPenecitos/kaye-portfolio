<template>
  <div class="max-w-6xl mx-auto px-4">
    <div class="flex flex-col gap-10">
      <section
        v-for="(category, index) in portfolio"
        :key="index"
        class="flex flex-col fade-in opacity-0 translate-y-10 transition-all duration-700 ease-out"
      >
        <TitlePage class="text-center text-[#0e221b] uppercase tracking-widest">
          {{ category.type.replace('-', ' ') }}
        </TitlePage>
        <div class="text-center text-[#0e221b] uppercase tracking-widest mb-10 text-2xl font-bold">
          {{ category.sub_type.replace('-', ' ') }}
        </div>

        <div v-if="category.type === 'social-media'" class="space-y-12">
          <div
            v-for="(contentGroup, cIndex) in category.content"
            :key="cIndex"
            class="flex flex-col gap-6 fade-in opacity-0 translate-y-10 transition-all duration-700 ease-out"
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
                class="w-full max-w-[200px] fade-in opacity-0 translate-y-10 transition-all duration-700 ease-out"
                :style="{ transitionDelay: `${iIndex * 100}ms` }"
              >
                <img
                  :src="item.file"
                  alt="Portfolio item"
                  class="h-full rounded-xl shadow-lg hover:scale-105 transition-transform duration-300 w-full"
                />
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import FontText from '@/components/FontText.vue'
import TitlePage from '@/components/TitlePage.vue'
import portData from '../json/portfolio.json'

const portfolio = ref(portData)

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add('opacity-100', 'translate-y-0')
          entry.target.classList.remove('opacity-0', 'translate-y-10')
        }
      })
    },
    { threshold: 0.2 },
  )

  const items = document.querySelectorAll('.fade-in')
  items.forEach((el) => observer.observe(el))
})
</script>

<!-- <script setup>
import { ref } from 'vue'
import FontText from '@/components/FontText.vue'
import TitlePage from '@/components/TitlePage.vue'
import portData from '../json/portfolio.json'

const portfolio = ref(portData)
</script> -->

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
