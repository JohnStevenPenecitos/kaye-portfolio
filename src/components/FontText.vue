<template>
  <div v-motion-fade-visible class="dark:text-white text-[#241b19]" :class="computedClasses">
    <p><slot /></p>
  </div>
</template>

<script setup>
import { computed, defineProps } from 'vue'

const props = defineProps({
  sizeVariant: {
    type: String,
    required: true,
    validator: (value) =>
      [
        'small',
        'smallbold',
        'medium',
        'large',
        'xl',
        'xlbold',
        'xxlbold',
        'largebold',
        'mediumbold',
        'mediumbolditalic',
      ].includes(value),
  },
  addedClass: {
    type: String,
    default: '',
  },
})

const sizeVariants = {
  small: 'text-sm md:text-base lg:text-lg',
  smallbold: 'text-sm md:text-base lg:text-lg font-bold my-3',

  medium: 'text-base md:text-lg lg:text-xl',
  mediumbold: 'text-base md:text-lg lg:text-xl font-bold',
  mediumbolditalic: 'text-base md:text-lg lg:text-xl font-bold italic',

  large: 'text-xl md:text-2xl lg:text-3xl',
  largebold: 'text-xl md:text-2xl lg:text-3xl font-bold',

  xl: 'text-3xl md:text-4xl lg:text-5xl',
  xlbold: 'text-3xl md:text-4xl lg:text-5xl font-semibold',

  xxlbold: 'text-4xl md:text-5xl lg:text-6xl font-semibold',
}

const computedClasses = computed(() => {
  return `${sizeVariants[props.sizeVariant]} ${props.addedClass}`.trim()
})
</script>
