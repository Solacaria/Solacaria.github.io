<template>
    <footer class="bg-gray-800 text-white py-8">
      <div class="container mx-auto px-4">
        <div class="flex flex-col md:flex-row justify-between items-center">
          <div class="mb-4 md:mb-0 place-items-start">
            <p class="text-lg font-semibold">Jonny Åhslund</p>
            <p class="text-gray-400">Junior Software Engineer</p>
          </div>
          <div class="flex space-x-4">
            <a href="https://www.linkedin.com/in/jonny-%C3%A5hslund-b3823a283/" class="text-gray-400 hover:text-white">
              <Linkedin class="h-5 w-5" />
            </a>
            <a href="https://github.com/Solacaria" class="text-gray-400 hover:text-white">
              <Github class="h-5 w-5" />
            </a>
            
            <a href="mailto:jonny.ahslund@live.se" class="text-gray-400 hover:text-white">
              <Mail class="h-5 w-5" />
            </a>
          </div>
        </div>
        <div class="mt-8 text-center text-gray-400 text-sm">
          <p>© {{ new Date().getFullYear() }} Jonny Åhslund. All rights reserved.</p>
        </div>
      </div>
    </footer>
</template>

<script setup>
import { Github, Linkedin, Mail } from 'lucide-vue-next';
</script>