<template>
    <section id="education" class="py-16 md:py-24 bg-gray-900">
      <div class="container mx-auto px-4">
        <h2 class="text-3xl font-bold text-center mb-12 text-gray-100">Educations</h2>
        
        <div class="max-w-3xl mx-auto">
          <div v-for="(course, index) in education" :key="index" class="mb-4">
            <div
              @click="toggleEduAccordion(index)"
              class="flex justify-between items-center p-4 bg-gray-800 rounded-md shadow-md cursor-pointer hover:bg-gray-700 transition-colors"
            >
              <div class="place-items-start">
                <h3 class="font-semibold text-lg text-gray-100">{{ course.title }}</h3>
                <p class="text-gray-300"> {{ course.extraInfo }} | {{ course.period }}</p>
              </div>
              <ChevronDown
                :class="{ 'transform rotate-180': course.isOpen }"
                class="h-5 w-5 text-gray-400 transition-transform duration-200"
              />
            </div>
            <div
              v-if="course.isOpen"
              class="bg-gray-800 p-4 rounded-b-md shadow-sm border-t border-gray-700 mt-px"
            >
              <p class="text-gray-300 mb-4 font-medium">{{ course.description }}</p>
              <ul class="list-disc pl-5 space-y-2">
                <li v-for="(className, rIndex) in course.classes" :key="rIndex" class="text-gray-300">
                  {{ className }}
                </li>
              </ul>
              <div v-if="course.technologies" class="mt-4">
                <p class="font-medium text-gray-200 mb-2">Technologies:</p>
                <div class="flex flex-wrap gap-2">
                  <span
                    v-for="(tech, tIndex) in course.technologies"
                    :key="tIndex"
                    class="px-3 py-1 bg-gray-700 text-gray-300 text-sm rounded-full"
                  >
                    {{ tech }}
                  </span>
                </div>
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

const education = ref ([
  /* Template
  {
    title: "",
    extraInfo: "",
    period: "",
    description: "",
    classes: [
      "", 
      "", 
      "",
    ],
    technologies: ["", "", "",], //Finns det tekniker? 
    isOpen: false
  },
  */
  {
    title: ".NET software developer",
    extraInfo: "Teknikhögskolan Gävle",
    period: "Aug 2023 - May 2025",
    description: "Learning the basics and advanced knowledge in C# and .NET",
    classes: [
      "Basic C#", 
      "Advanced C#", 
      "JavaScript basics", 
      "Basics in frontend", 
      "SQL server", 
      "Microsoft Cloud",
    ],
    technologies: ["JavaScript", "HTML/CSS", "React.js", "C#", "Entity Framework Core", "MAUI basics"], //Finns det tekniker? 
    isOpen: false
  },
  {
    title: "Forklift Certification",
    extraInfo: "Arlanda",    period: "2018",
    description: "Learning how to safetly operate a forklift",
    classes: [
      "A1, A2, A3, A4", 
      "B1, B2, B3, B6", 
      "D1, D2"
    ],
    //technologies: ["", "", "",], //Finns det tekniker? 
    isOpen: false
  },
  {
    title: "High school education",
    extraInfo: "Tierp",
    period: "2007-2010",
    description: "Electrician",
    classes: [
      "Basic Electrical Theory - Understanding of electricity, circuits, voltage, current, resistance, and power.", 
      "Wiring and Circuit Design - Learning to design, install, and troubleshoot electrical wiring for residential, commercial, and industrial buildings", 
      "Electrical Safety - Understanding electrical codes, regulations, and safety procedures to work safely with high-voltage equipment.",
      "Motor Control and Automation - Learning to work with motors, controls, and automated systems",
      "Lighting Systems - Study and installation of lighting systems, including energy-efficient lighting like LED and smart lighting.",
      "Power Distribution Systems - Understanding how electrical power is distributed in buildings and industrial systems, including panelboards and transformers.",
    ],
    technologies: ["BB1 certified",], //Finns det tekniker? 
    isOpen: false
  },
]);

const toggleEduAccordion = (index) => {
  education.value[index].isOpen = !education.value[index].isOpen;
};
</script>