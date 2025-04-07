<template>
    <section id="projects" class="py-16 md:py-24 bg-gray-900">
      <div class="container mx-auto px-4">
        <h2 class="text-3xl font-bold text-center mb-12 text-gray-100">My Projects</h2>
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div v-for="(project, index) in projects" :key="index" class="bg-gray-800 rounded-lg overflow-hidden shadow-md hover:shadow-lg transition-shadow">
            <div class="h-48 bg-gray-700 relative">
              <img
                :src="project.image"
                :alt="project.title"
                class="w-full h-full object-cover"
              />
            </div>
            <div class="p-6">
              <h3 class="font-bold text-xl mb-2 text-gray-100">{{ project.title }}</h3>
              <p class="text-gray-300 mb-4">{{ project.description }}</p>
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
import { Menu, X, ChevronDown, ExternalLink, Github, Mail, Linkedin, Twitter, MapPin } from 'lucide-vue-next';

const projects = ref([
  /* Template
  {
    title: '',
    description: '',
    image: 'https://via.placeholder.com/600x400',
    technologies: ['', '', '',],
    demo: 'https://example.com/demo1',
    github: 'https://github.com/yourusername/project1'
  },
  */
  {
    title: 'Digital cookbook',
    description: 'Add, remove, edit and save recipes with ease. Has search function for tags and title. Follows the MVVC pattern',
    image: '../src/assets/test_image.png',
    technologies: ['MAUI', 'C#', 'XAML', ],
    demo: '',
    github: 'https://github.com/Solacaria/PP-MAUI-Cookbook-WIP'
  },
]);

</script>