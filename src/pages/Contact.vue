<template>
  <div class="max-w-4xl mx-auto w-full">
    <TitlePage> Contact Me! </TitlePage>
    <form
      @submit.prevent="sendEmail"
      ref="formRef"
      class="flex flex-col gap-6 w-full bg-white/70 backdrop-blur-md shadow-lg p-10 rounded-2xl"
    >
      <div class="flex flex-col gap-2">
        <label class="font-semibold text-gray-700">Full Name</label>
        <input
          v-model="form.name"
          name="user_name"
          type="text"
          required
          placeholder="Enter your name"
          class="p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-[#7a685d] outline-none"
        />
      </div>

      <div class="flex flex-col gap-2">
        <label class="font-semibold text-gray-700">Email Address</label>
        <input
          v-model="form.email"
          name="user_email"
          type="email"
          required
          placeholder="Enter your email"
          class="p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-[#7a685d] outline-none"
        />
      </div>

      <div class="flex flex-col gap-2">
        <label class="font-semibold text-gray-700">Message</label>
        <textarea
          v-model="form.message"
          name="message"
          required
          placeholder="Write your message..."
          rows="5"
          class="p-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-[#7a685d] outline-none"
        ></textarea>
      </div>

      <button
        type="submit"
        class="bg-[#7a685d] hover:bg-[#5b4c43] text-white font-semibold py-3 px-6 rounded-lg transition duration-200"
      >
        Send Message
      </button>

      <p v-if="statusMessage" class="text-center text-sm text-gray-600 mt-3">
        {{ statusMessage }}
      </p>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import emailjs from 'emailjs-com'
import TitlePage from '@/components/TitlePage.vue'

const form = ref({
  name: '',
  email: '',
  message: '',
})
const formRef = ref(null)
const statusMessage = ref('')

const sendEmail = () => {
  emailjs
    .sendForm(
      'YOUR_SERVICE_ID', // from EmailJS dashboard
      'YOUR_TEMPLATE_ID', // from EmailJS dashboard
      formRef.value,
      'YOUR_PUBLIC_KEY', // from EmailJS dashboard
    )
    .then(
      () => {
        statusMessage.value = '✅ Your message has been sent successfully!'
        form.value = { name: '', email: '', message: '' }
      },
      (error) => {
        console.error(error)
        statusMessage.value = '❌ Failed to send message. Please try again later.'
      },
    )
}
</script>
