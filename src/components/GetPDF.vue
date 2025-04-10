<template>
    <div class="flex flex-col items-start space-y-4">
      <label for="cvLanguage" class="text-lg font-semibold text-gray-100">
        Download CV as PDF: 
      </label>
      <select
        id="cvLanguage"
        v-model="selectedLanguage"
        class="border border-gray-300 rounded-md px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500 text-gray-200 bg-gray-900"
      >
        <option disabled value="">-- Select language --</option>
        <option value="en">English</option>
        <option value="sv">Swedish</option>
      </select>
  
      <button
        :disabled="!selectedLanguage"
        @click="downloadCv"
        class="bg-blue-600 text-white min-w-[200px] px-6 py-2 rounded-md font-semibold flex items-center justify-center 
                space-x-2 transition duration-200 disabled:opacity-50 disabled:cursor-not-allowed hover:bg-blue-700
                "
        >
            <FileText class="w-5 h-5" />
            <span>Download</span>
        </button>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  import {FileText} from 'lucide-vue-next';
  
  const selectedLanguage = ref('')
  
  const downloadCv = () => {
    const file = selectedLanguage.value === 'en'
      ? '/Jonny_Åhslund_CV_eng.pdf'
      : '/Jonny_Åhslund_CV_swe.pdf'
  
    const link = document.createElement('a')
    link.href = file
    link.download = file.split('/').pop()
    document.body.appendChild(link)
    link.click()
    document.body.removeChild(link)
  }
  </script>
  