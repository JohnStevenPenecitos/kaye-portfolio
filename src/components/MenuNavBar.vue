<template>
  <div class="bg-white/30 backdrop-blur-sm fixed top-0 left-0 w-full z-50">
    <nav class="flex md:justify-center justify-end items-center px-4 py-2 text-[#7a685d]">
      <div class="hidden md:flex gap-8 items-center">
        <RouterLink
          v-for="link in links"
          :key="link.path"
          :to="link.path"
          :class="[
            'p-2 rounded-full transition-all duration-200',
            'dark:hover:bg-gray-800 hover:bg-gray-200',
            isActive(link.path) ? 'font-bold bg-gray-200 dark:bg-gray-800' : 'font-normal',
          ]"
        >
          {{ link.name }}
        </RouterLink>
      </div>

      <button
        @click="isOpen = !isOpen"
        class="md:hidden p-2 rounded-lg hover:bg-gray-200 dark:hover:bg-gray-800"
      >
        <svg
          v-if="!isOpen"
          xmlns="http://www.w3.org/2000/svg"
          class="h-7 w-7"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M4 6h16M4 12h16M4 18h16"
          />
        </svg>

        <svg
          v-else
          xmlns="http://www.w3.org/2000/svg"
          class="h-7 w-7"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M6 18L18 6M6 6l12 12"
          />
        </svg>
      </button>
    </nav>

    <div
      v-if="isOpen"
      class="md:hidden flex flex-col items-center bg-white/30 backdrop-blur-sm py-2 space-y-2 text-[#7a685d]"
    >
      <RouterLink
        v-for="link in links"
        :key="link.path"
        :to="link.path"
        class="p-2 w-full text-center rounded-lg hover:bg-gray-200 dark:hover:bg-gray-800"
        :class="[isActive(link.path) ? 'font-bold bg-gray-200 dark:bg-gray-800' : 'font-normal']"
        @click="isOpen = false"
      >
        {{ link.name }}
      </RouterLink>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()

const isOpen = ref(false)

const links = [
  { name: 'Home', path: '/' },
  { name: 'About', path: '/about' },
  { name: 'Portfolio', path: '/portfolio' },
  { name: 'Contact', path: '/contact' },
]

const isActive = (path) => route.path === path
</script>
