<template>
  <div class="max-w-4xl mx-auto">
    <TitlePage> About Me </TitlePage>
    <div class="flex flex-col gap-10">
      <div class="h-[40rem] bg-red-300 flex flex-col justify-center items-center">
        <div class="flex flex-col">
          <section class="flex flex-col justify-center items-center gap-8">
            <div class="flex gap-10">
              <img
                class="w-[300px] rounded-t-full border-4 border-[#7a685d] shadow-md"
                :src="kaye"
                alt=""
              />
              <div class="flex justify-center items-center">
                <FontText addedClass=" my-4 leading-relaxed" sizeVariant="large">
                  <span class="font-semibold"
                    >A passionate Canva designer and video editor who brings ideas to life through
                    creative visuals, smooth edits, and a touch of storytelling flair. A passionate
                    Canva designer and video editor who brings ideas to life through creative
                    visuals, smooth edits, and a touch of storytelling flair.
                  </span>
                </FontText>
              </div>
            </div>
          </section>
        </div>
      </div>

      <!-- Education -->
      <section class="flex flex-col justify-center items-center gap-8 bg-red-200 h-[45rem]">
        <FontText addedClass="text-center" sizeVariant="xxlbold"> Education🎓 </FontText>
        <div class="relative dark:border-zinc-600 space-y-10 w-full">
          <div v-for="(educ, index) in education" :key="index" class="relative">
            <div class="flex justify-between">
              <div class="flex flex-col justify-center items-center gap-2 bg-blue-300">
                <div class="flex gap-2">
                  <div class="flex justify-center items-center">
                    <img class="w-16 h-16" :src="educ.icon" alt="" />
                  </div>
                  <div>
                    <FontText addedClass="" sizeVariant="largebold"> {{ educ.name }}</FontText>
                    <FontText addedClass="  " sizeVariant="mediumbold"> {{ educ.course }}</FontText>
                  </div>
                </div>
              </div>
              <FontText addedClass=" my-4" sizeVariant="mediumbold"> {{ educ.year }}</FontText>
            </div>
          </div>
        </div>
      </section>

      <!-- Experiences -->
      <section class="flex flex-col justify-center items-center gap-8 px-10">
        <FontText addedClass="text-center my-10" sizeVariant="xxlbold"> Experiences🎓 </FontText>
        <div class="relative space-y-10 w-full border-l-4 border-[#7a685d]">
          <div v-for="(exp, index) in experiences" :key="index" class="relative">
            <div class="flex justify-between">
              <div class="flex flex-col justify-center items-center gap-2 relative">
                <div class="flex relative">
                  <div class="flex justify-center items-center">
                    <img
                      class="w-14 h-14 absolute -left-[30px] top-0 border-[#7a685d] border-2 rounded-full"
                      :src="exp.icon"
                      alt=""
                    />
                  </div>
                  <div class="pl-8">
                    <FontText sizeVariant="largebold"> {{ exp.position }}</FontText>
                    <FontText sizeVariant="mediumbold"> {{ exp.name }}</FontText>
                    <ul class="list-disc mt-2 space-y-1 pl-4">
                      <li v-for="(desc, dIndex) in exp.description" :key="dIndex">
                        <FontText sizeVariant="small">
                          {{ desc.name }}
                        </FontText>
                      </li>
                    </ul>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Skills -->
      <section class="flex flex-col justify-center items-center gap-8 mt-20">
        <FontText addedClass="" sizeVariant="xxlbold"> What I do </FontText>
        <div class="grid md:grid-cols-2 gap-10 text-gray-700 text-lg">
          <div
            v-for="(item, index) in skills"
            :key="index"
            class="bg-[#d49f7b] shadow-[8px_8px_0px_rgba(0,0,0,1)] shadow-zinc-200 rounded-2xl p-6 hover:shadow-lg transition"
          >
            <div class="flex flex-col items-center">
              <Icons :icon="item.icon" />
              <FontText addedClass="text-[#0e221b] my-4" sizeVariant="mediumbold">
                {{ item.name }}</FontText
              >
              <FontText addedClass="text-[#0e221b]" sizeVariant="small">
                {{ item.description }}</FontText
              >
            </div>
          </div>
        </div>
      </section>

      <!-- Tools -->
      <!-- <section class="flex flex-col justify-center items-center gap-8 my-20">
        <FontText addedClass="" sizeVariant="xxlbold"> Tools </FontText>
        <div class="flex">
          <div class="grid md:grid-cols-2 gap-10 text-gray-700 text-lg">
            <div v-for="(item, index) in tools" :key="index" class="flex flex-col items-center">
              <Icons :icon="item.icon" />
              <FontText addedClass="text-[#0e221b] my-4" sizeVariant="mediumbold">
                {{ item.name }}</FontText
              >
            </div>
          </div>
          <div class="grid md:grid-cols-2 gap-10 text-gray-700 text-lg">
            <div v-for="(item, index) in tools" :key="index" class="flex flex-col items-center">
              <Icons :icon="item.icon" />
              <FontText addedClass="text-[#0e221b] my-4" sizeVariant="mediumbold">
                {{ item.name }}</FontText
              >
            </div>
          </div>
        </div>
      </section> -->

      <section class="flex flex-col justify-center items-center gap-8 my-20">
        <FontText addedClass="" sizeVariant="xxlbold"> Tools </FontText>
        <div class="grid md:grid-cols-2 gap-10">
          <div
            v-for="(category, index) in tools"
            :key="index"
            class="w-full flex flex-col items-center justify-center"
          >
            <FontText
              sizeVariant="xlbold"
              addedClass="text-center text-[#0e221b]  uppercase tracking-widest"
            >
              {{ category.type.replace('_', ' ') }}
            </FontText>

            <div class="grid md:grid-cols-2 gap-6 w-full max-w-3xl">
              <div
                v-for="(contentGroup, cIndex) in category.content"
                :key="cIndex"
                class="flex items-center justify-center hover:scale-105 transition-transform duration-300"
              >
                <div class="flex flex-col gap-2">
                  <Icons :icon="contentGroup.icon" />
                  <FontText
                    sizeVariant="largebold"
                    addedClass="capitalize text-center text-[#7a685d]"
                  >
                    {{ contentGroup.name }}
                  </FontText>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import FontText from '@/components/FontText.vue'
// import kaye from '/kayi.jpg'
import kaye from '/flyers/1.png'

import TitlePage from '@/components/TitlePage.vue'

import educData from '../json/education.json'
import expeData from '../json/experiences.json'
import skillData from '../json/skills.json'
import toolData from '../json/tools.json'

import Icons from '@/components/Icons.vue'

const education = ref(educData)
const experiences = ref(expeData)
const skills = ref(skillData)
const tools = ref(toolData)
</script>
