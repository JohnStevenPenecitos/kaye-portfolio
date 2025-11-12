<template>
  <div class="bg-white/30 backdrop-blur-sm transition-opacity fixed top-0 left-0 w-full z-50">
    <nav class="flex gap-8 justify-center items-center text-[#7a685d] p-2">
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
    </nav>
  </div>
</template>

<script setup>
import { useRoute } from 'vue-router'

const route = useRoute()

const links = [
  { name: 'Home', path: '/' },
  { name: 'About', path: '/about' },
  { name: 'Portfolio', path: '/portfolio' },
  { name: 'Contact', path: '/contact' },
]

const isActive = (path) => route.path === path
</script>
