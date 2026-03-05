<template>
  <section id="projects" class="py-16 md:py-24 bg-gray-900">
    <div class="container mx-auto px-4">
      <h2 class="text-3xl font-bold text-center mb-12 text-gray-100">My Projects</h2>

      <div class="flex flex-wrap justify-center gap-8">
        <div
          v-for="(project, index) in projects" :key="index"
            class="w-full md:w-[48%] lg:w-[30%] bg-gray-800 rounded-lg overflow-hidden shadow-md hover:shadow-lg transition-shadow">
          <div class="h-48 bg-gray-700 relative">
            <img
              :src="project.image"
              :alt="project.title"
              class="w-full h-full object-cover"
            />
            </div>
            <div class="p-6">
              <h3 class="font-bold text-xl mb-2 text-gray-100">{{ project.title }}</h3>
              <p class="text-gray-300 mb-4">
                {{ project.description }}
                <a :href="project.linkUrl" class="text-blue-400 underline" target="_blank">
                  <br>{{ project.linkText }}
                </a>
              </p>
              <div class="flex flex-wrap gap-2 mb-4">
                <span
                  v-for="(tech, tIndex) in project.technologies"
                  :key="tIndex"
                  class="px-2 py-1 bg-gray-700 text-gray-300 text-xs rounded-full"
                >
                  {{ tech }}
                </span>
              </div>
              <div class="flex space-x-3">
                <a
                  v-if="project.demo"
                  :href="project.demo"
                  target="_blank"
                  rel="noopener noreferrer"
                  class="text-emerald-400 hover:text-emerald-500 flex items-center"
                >
                  <ExternalLink class="h-4 w-4 mr-1" />
                  Demo
                </a>
                <a
                  v-if="project.github"
                  :href="project.github"
                  target="_blank"
                  rel="noopener noreferrer"
                  class="text-gray-300 hover:text-gray-400 flex items-center"
                >
                  <Github class="h-4 w-4 mr-1" />
                  Code
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
</template>

<script setup>
import { ref } from 'vue';
import { ExternalLink, Github } from 'lucide-vue-next';

import cookbookImg from '../assets/Kokboken-front.jpg';
import guildBankImg from '../assets/GuildBankViewer-front.jpg';
import discordBotImg from '../assets/Discord-bot-img.png';

const projects = ref([
  /* Template
  {
    title: '',
    description: '',
    linkText: '',
    linkUrl: '',
    image: 'https://via.placeholder.com/600x400',
    technologies: ['', '', '',],
    demo: 'https://example.com/demo1',
    github: 'https://github.com/yourusername/project1'
  },
  */
  {
    title: 'Digital cookbook (WIP)',
    description: 'First ever solo project to test myself. Features: Add, remove, edit and save recipes with ease. Has search function for tags and title. Follows the MVVC pattern.',
    image: cookbookImg,
    technologies: ['MAUI', 'C#', 'XAML', ],
    demo: '',
    github: 'https://github.com/Solacaria/PP-MAUI-Cookbook-WIP'
  },
  {
    title: "Guild Bank Viewer",
    description: "A website to view data and a World of Warcraft addon to export the data." +
      "\nDisplays the data from World of Warcraft guild bank in tables and allows you to search tabs, players and more." +
      "\nThe website is built with Vue.js, while the addon is written in Lua.",
    image: guildBankImg,
    technologies: ['Vue.js', 'Lua', 'CSS', 'HTML', 'JavaScript' ],
    demo: 'https://guild-bank-viewer.vercel.app/',
    github: 'https://github.com/Solacaria/Guild_Bank_Viewer'
  },
  {
    title: "Discord bot",
    description: "A bot to help find groups of players for ingame activities in world of warcraft." +
      "\nI dont take full credit for this bot, i have however made some major changes to make it fit and work for our specific discord needs.",
    linkText: "Original code by Baddadan/Kashual for NoP EU.",
    linkUrl: "https://bit.ly/3ZrVj7C",
    image: discordBotImg,
    technologies: ['JavaScript' ],
    demo: '',
    github: 'https://github.com/Solacaria/Dungeon-Buddy-master'
  }
  
]);
</script>