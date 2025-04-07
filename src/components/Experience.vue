<template>
    <section id="experience" class="py-16 md:py-24 bg-gray-900">
      <div class="container mx-auto px-4">
        <h2 class="text-3xl font-bold text-center mb-12 text-gray-100">Work Experience</h2>
        
        <div class="max-w-3xl mx-auto">
          <div v-for="(job, index) in experience" :key="index" class="mb-4">
            <div
              @click="toggleExpAccordion(index)"
              class="flex justify-between items-center p-4 bg-gray-800 rounded-md shadow-md cursor-pointer hover:bg-gray-700 transition-colors"
            >
              <div class="place-items-start">
                <h3 class="font-semibold text-lg text-gray-100">{{ job.title }}</h3>
                <p class="text-gray-400">{{ job.company }} | {{ job.period }}</p>
              </div>
              <ChevronDown
                :class="{ 'transform rotate-180': job.isOpen }"
                class="h-5 w-5 text-gray-300 transition-transform duration-200"
              />
            </div>
            <div
              v-if="job.isOpen"
              class="bg-gray-800 p-4 rounded-b-md shadow-sm border-t border-gray-700 mt-px"
            >
              <p class="text-gray-300 mb-4 font-medium">{{ job.description }}</p>
              <ul class="list-disc pl-5 space-y-2">
                <li v-for="(responsibility, rIndex) in job.responsibilities" :key="rIndex" class="text-gray-400">
                  {{ responsibility }}
                </li>
              </ul>
              <div v-if="job.technologies" class="mt-4">
                <p class="font-medium text-gray-300 mb-2">Technologies:</p>
                <div class="flex flex-wrap gap-2">
                  <span
                    v-for="(tech, tIndex) in job.technologies"
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


const experience = ref([

  /*template
  {
    title: "",
    company: "",
    period: "",
    description: "",
    responsibilities: [
    "", 
    "", 
    "",
    ],
    technologies: ["", "", ""], //Finns det tekniker? 
    isOpen: false,
  },
  */
  {
    title: "Learning at Work / Internship",
    company: "Vitec Software Group",
    period: "10 Feb 2025 - 9 May 2025",
    description: "Modernizing product code",
    responsibilities: [
    "Migrating backend to .NET 9 core from 4.8", 
    "Setting up new endpoint controllers",
    "Improving performance by removing redundant code",
    "Migrating frontend from webforms to Vue 3", 
    ],
    technologies: [".NET 4.8", ".NET 9", "Vue", "Webforms", "JavaScript"], //Finns det tekniker? 
    isOpen: false,
  },
  {
    title: "Learning at Work / Internship",
    company: "Arcledi OÜ",
    period: "7 Oct 2024 - 29 Nov 2024",
    description: "Startup company - Barter service",
    responsibilities: [
      "Developed backend for the website",
      "Developed cloud functions in Firebase",
      "Structured a NoSQL database",
      "Login system with role management for users"
    ],
    technologies: ["JavaScript", "NoSQL Database", "Cloud Development", "Serverless Architecture"], 
    isOpen: false,
  },
  {
    title: "Maintenance Manager",
    company: "Keolis",
    period: "June 2022 - April 2024",
    description: "Responsible for staff and inventory",
    responsibilities: [
      "Planning of repairs/refurbishments",
      "Post-inspection of buses",
      "Ensuring routines for staff",
      "Digitization of documents",
    ],
    technologies: ["MS Excell", "MS Word", ], 
    isOpen: false,
  },
  {
    title: "Service Technician",
    company: "Nobina",
    period: "May 2021 - June 2022",
    description: "Safety inspection of buses",
    responsibilities: [
    "Checking functionality of exterior lamps and headlights", 
    "Refilling fluids, diesel/AD-blue/oil ect", 
    "Making sure breaks and steering servo are working properly",
    "Minor repairs to seats, wipers and exterior lighting",
    "Removal of graffiti, stickers and garbage",
    ],
    //technologies: ["", "", ""], 
    isOpen: false,
  },
  {
    title: "Cargo Handler",
    company: "Spirit Air Cargo Handling",
    period: "Jan 2018 - Aug 2019",
    description: "Cargo handling for air freight",
    responsibilities: [
      "Handling of air freight, including sorting, storage, pallet building, and delivery to customers",
      "Delivered to/from aircrafts, in cooperation with Bring",
      "Mail handling for both local and global transport",
      "Handling valuable goods, such as medical equipment or gold",
    ],
    technologies: ["Forklift certified for A, B and D", "Security clearance by SÄPO", "PIL-certified"] , //Finns det tekniker? 
    isOpen: false,
  },
  //#region examples, AI generated
  // {
  //   title: 'Senior Software Engineer',
  //   company: 'Tech Company',
  //   period: 'Jan 2021 - Present',
  //   description: 'Led the development of a complex web application that improved customer engagement by 40%.',
  //   responsibilities: [
  //     'Architected and implemented new features using Vue.js and Node.js',
  //     'Mentored junior developers and conducted code reviews',
  //     'Optimized application performance, reducing load time by 30%',
  //     'Collaborated with product managers to define and prioritize features'
  //   ],
  //   technologies: ['Vue.js', 'Node.js', 'TypeScript', 'MongoDB', 'Docker'],
  //   isOpen: false
  // },
  // {
  //   title: 'Software Developer',
  //   company: 'Digital Agency',
  //   period: 'Mar 2018 - Dec 2020',
  //   description: 'Worked on multiple client projects, delivering high-quality web applications on time and within budget.',
  //   responsibilities: [
  //     'Developed responsive web applications using React and Vue.js',
  //     'Implemented RESTful APIs using Express.js',
  //     'Collaborated with designers to implement pixel-perfect UI',
  //     'Participated in agile development processes'
  //   ],
  //   technologies: ['React', 'Vue.js', 'Express.js', 'PostgreSQL', 'AWS'],
  //   isOpen: false
  // },
  // {
  //   title: 'Junior Web Developer',
  //   company: 'Startup Inc.',
  //   period: 'Jun 2016 - Feb 2018',
  //   description: 'Contributed to the development of the company\'s main product, a SaaS platform for project management.',
  //   responsibilities: [
  //     'Built and maintained frontend components using Angular',
  //     'Implemented responsive designs and ensured cross-browser compatibility',
  //     'Fixed bugs and improved application performance',
  //     'Participated in daily stand-ups and sprint planning'
  //   ],
  //   technologies: ['Angular', 'JavaScript', 'CSS', 'HTML', 'Git'],
  //   isOpen: false
  // }
  //#endregion
]);

const toggleExpAccordion = (index) => {
  experience.value[index].isOpen = !experience.value[index].isOpen;
};
</script>