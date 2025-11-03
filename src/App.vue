<script setup>
import { ref } from 'vue'
import MenuNavBar from './components/MenuNavBar.vue'
// import ThemeSelector from './components/ThemeSelector.vue'

// const blobs = ref([
//   { id: 1, size: '500px', top: '10%', left: '20%', color: 'rgba(173, 232, 213, 0.8)' },
//   { id: 2, size: '550px', top: '40%', left: '65%', color: 'rgba(192, 160, 255, 0.8)' },
//   { id: 3, size: '500px', top: '70%', left: '30%', color: 'rgba(255, 182, 193, 0.8)' },
//   { id: 4, size: '500px', top: '0%', left: '70%', color: 'rgba(255, 182, 250, 0.8)' },
// ])
</script>

<template>
  <div class="relative flex flex-col font-display min-h-screen bg-[#f2eddb]">
    <main class="gap-2 transition-all duration-300 flex flex-col flex-1 h-full">
      <MenuNavBar />
      <div class="flex-1 lg:px-56 px-0 flex justify-center">
        <RouterView />
      </div>
    </main>
    <!-- <ThemeSelector /> -->
  </div>
</template>

<style scoped>
html {
  scroll-behavior: smooth;
}
</style>
