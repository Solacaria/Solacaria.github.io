<template>
  <div class="min-h-screen bg-gray-50">
    <!-- Navigation -->
    <nav class="bg-white shadow-sm">
      <div class="container mx-auto px-4 py-4 flex justify-between items-center">
        <div class="text-xl font-bold text-gray-800">Your Name</div>
        <div class="hidden md:flex space-x-6">
          <a href="#about" class="text-gray-600 hover:text-gray-900">About</a>
          <a href="#experience" class="text-gray-600 hover:text-gray-900">Experience</a>
          <a href="#projects" class="text-gray-600 hover:text-gray-900">Projects</a>
          <a href="#contact" class="text-gray-600 hover:text-gray-900">Contact</a>
        </div>
        <button @click="mobileMenuOpen = !mobileMenuOpen" class="md:hidden">
          <Menu v-if="!mobileMenuOpen" class="h-6 w-6 text-gray-600" />
          <X v-else class="h-6 w-6 text-gray-600" />
        </button>
      </div>
      <!-- Mobile menu -->
      <div v-if="mobileMenuOpen" class="md:hidden bg-white py-2 px-4">
        <div class="flex flex-col space-y-3">
          <a href="#about" class="text-gray-600 hover:text-gray-900" @click="mobileMenuOpen = false">About</a>
          <a href="#experience" class="text-gray-600 hover:text-gray-900" @click="mobileMenuOpen = false">Experience</a>
          <a href="#projects" class="text-gray-600 hover:text-gray-900" @click="mobileMenuOpen = false">Projects</a>
          <a href="#contact" class="text-gray-600 hover:text-gray-900" @click="mobileMenuOpen = false">Contact</a>
        </div>
      </div>
    </nav>

    <!-- Hero Section -->
    <section id="about" class="py-16 md:py-24 bg-white">
      <div class="container mx-auto px-4">
        <div class="flex flex-col md:flex-row items-center">
          <div class="md:w-1/2 mb-8 md:mb-0">
            <div class="relative w-64 h-64 mx-auto md:mx-0 rounded-full overflow-hidden border-4 border-gray-200">
              <img
                src="https://via.placeholder.com/400x400"
                alt="Your Profile"
                class="w-full h-full object-cover"
              />
            </div>
          </div>
          <div class="md:w-1/2 md:pl-12">
            <h1 class="text-4xl md:text-5xl font-bold text-gray-800 mb-4">
              Hi, I'm <span class="text-emerald-600">Your Name</span>
            </h1>
            <h2 class="text-2xl text-gray-600 mb-6">Software Engineer</h2>
            <p class="text-gray-600 mb-8 leading-relaxed">
              I'm a passionate software engineer with expertise in building modern web applications.
              I specialize in frontend and backend development, with a focus on creating
              scalable, maintainable, and user-friendly applications.
            </p>
            <div class="flex space-x-4">
              <a
                href="#contact"
                class="px-6 py-3 bg-emerald-600 text-white rounded-md hover:bg-emerald-700 transition-colors"
              >
                Contact Me
              </a>
              <a
                href="#projects"
                class="px-6 py-3 border border-gray-300 text-gray-700 rounded-md hover:bg-gray-50 transition-colors"
              >
                View Projects
              </a>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Experience Section -->
    <section id="experience" class="py-16 md:py-24 bg-gray-50">
      <div class="container mx-auto px-4">
        <h2 class="text-3xl font-bold text-center mb-12 text-gray-800">Work Experience</h2>
        
        <div class="max-w-3xl mx-auto">
          <div v-for="(job, index) in experience" :key="index" class="mb-4">
            <div
              @click="toggleAccordion(index)"
              class="flex justify-between items-center p-4 bg-white rounded-md shadow-sm cursor-pointer hover:bg-gray-50 transition-colors"
            >
              <div>
                <h3 class="font-semibold text-lg text-gray-800">{{ job.title }}</h3>
                <p class="text-gray-600">{{ job.company }} | {{ job.period }}</p>
              </div>
              <ChevronDown
                :class="{ 'transform rotate-180': job.isOpen }"
                class="h-5 w-5 text-gray-500 transition-transform duration-200"
              />
            </div>
            <div
              v-if="job.isOpen"
              class="bg-white p-4 rounded-b-md shadow-sm border-t border-gray-100 mt-px"
            >
              <p class="text-gray-600 mb-4">{{ job.description }}</p>
              <ul class="list-disc pl-5 space-y-2">
                <li v-for="(responsibility, rIndex) in job.responsibilities" :key="rIndex" class="text-gray-600">
                  {{ responsibility }}
                </li>
              </ul>
              <div v-if="job.technologies" class="mt-4">
                <p class="font-medium text-gray-700 mb-2">Technologies:</p>
                <div class="flex flex-wrap gap-2">
                  <span
                    v-for="(tech, tIndex) in job.technologies"
                    :key="tIndex"
                    class="px-3 py-1 bg-gray-100 text-gray-700 text-sm rounded-full"
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

    <!-- Projects Section -->
    <section id="projects" class="py-16 md:py-24 bg-white">
      <div class="container mx-auto px-4">
        <h2 class="text-3xl font-bold text-center mb-12 text-gray-800">My Projects</h2>
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div v-for="(project, index) in projects" :key="index" class="bg-white rounded-lg overflow-hidden shadow-md hover:shadow-lg transition-shadow">
            <div class="h-48 bg-gray-200 relative">
              <img
                :src="project.image"
                :alt="project.title"
                class="w-full h-full object-cover"
              />
            </div>
            <div class="p-6">
              <h3 class="font-bold text-xl mb-2 text-gray-800">{{ project.title }}</h3>
              <p class="text-gray-600 mb-4">{{ project.description }}</p>
              <div class="flex flex-wrap gap-2 mb-4">
                <span
                  v-for="(tech, tIndex) in project.technologies"
                  :key="tIndex"
                  class="px-2 py-1 bg-gray-100 text-gray-700 text-xs rounded-full"
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
                  class="text-emerald-600 hover:text-emerald-700 flex items-center"
                >
                  <ExternalLink class="h-4 w-4 mr-1" />
                  Demo
                </a>
                <a
                  v-if="project.github"
                  :href="project.github"
                  target="_blank"
                  rel="noopener noreferrer"
                  class="text-gray-700 hover:text-gray-900 flex items-center"
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

    <!-- Contact Section -->
    <section id="contact" class="py-16 md:py-24 bg-gray-50">
      <div class="container mx-auto px-4">
        <h2 class="text-3xl font-bold text-center mb-12 text-gray-800">Get In Touch</h2>
        
        <div class="max-w-3xl mx-auto bg-white rounded-lg shadow-md p-8">
          <div class="flex flex-col md:flex-row md:space-x-8">
            <div class="md:w-1/2 mb-8 md:mb-0">
              <h3 class="text-xl font-semibold mb-4 text-gray-800">Contact Information</h3>
              <div class="space-y-4">
                <div class="flex items-center">
                  <Mail class="h-5 w-5 text-emerald-600 mr-3" />
                  <a href="mailto:jonny.ahslund@live.se" class="text-gray-600 hover:text-emerald-600">
                    E-mail: Jonny.ahslund@live.se
                  </a>
                </div>
                <div class="flex items-center">
                  <Linkedin class="h-5 w-5 text-emerald-600 mr-3" />
                  <a href="https://linkedin.com/in/yourprofile" target="_blank" rel="noopener noreferrer" class="text-gray-600 hover:text-emerald-600">
                    linkedin.com/in/yourprofile
                  </a>
                </div>
                <div class="flex items-center">
                  <Github class="h-5 w-5 text-emerald-600 mr-3" />
                  <a href="https://github.com/Solacaria" target="_blank" rel="noopener noreferrer" class="text-gray-600 hover:text-emerald-600">
                    Solacaria @ Github
                  </a>
                </div>
                <div class="flex items-center">
                  <MapPin class="h-5 w-5 text-emerald-600 mr-3" />
                  <span class="text-gray-600">Tierp, Sweden</span>
                </div>
              </div>
            </div>
            
            <div class="md:w-1/2">
              <h3 class="text-xl font-semibold mb-4 text-gray-800">Send Me a Message</h3>
              <form @submit.prevent="submitForm" class="space-y-4">
                <div>
                  <label for="name" class="block text-sm font-medium text-gray-700 mb-1">Name</label>
                  <input
                    id="name"
                    v-model="contactForm.name"
                    type="text"
                    class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-emerald-500 focus:border-transparent"
                    required
                  />
                </div>
                <div>
                  <label for="subject" class="block text-sm font-medium text-gray-700 mb-1">Subject</label>
                  <input
                    id="subject"
                    v-model="contactForm.subject"
                    type="text"
                    class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-emerald-500 focus:border-transparent"
                    required
                  />
                </div>
                <div>
                  <label for="email" class="block text-sm font-medium text-gray-700 mb-1">Email</label>
                  <input
                    id="email"
                    v-model="contactForm.email"
                    type="email"
                    class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-emerald-500 focus:border-transparent"
                    required
                  />
                </div>
                <div>
                  <label for="message" class="block text-sm font-medium text-gray-700 mb-1">Message</label>
                  <textarea
                    id="message"
                    v-model="contactForm.message"
                    rows="4"
                    class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-emerald-500 focus:border-transparent"
                    required
                  ></textarea>
                </div>
                <button
                  type="submit"
                  class="w-full px-4 py-2 bg-emerald-600 text-white rounded-md hover:bg-emerald-700 transition-colors focus:outline-none focus:ring-2 focus:ring-emerald-500 focus:ring-offset-2"
                >
                  Send Message
                </button>
              </form>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="bg-gray-800 text-white py-8">
      <div class="container mx-auto px-4">
        <div class="flex flex-col md:flex-row justify-between items-center">
          <div class="mb-4 md:mb-0">
            <p class="text-lg font-semibold">Jonny Åhslund</p>
            <p class="text-gray-400">Software Engineer</p>
          </div>
          <div class="flex space-x-4">
            <a href="#" class="text-gray-400 hover:text-white">
              <Linkedin class="h-5 w-5" />
            </a>
            <a href="#" class="text-gray-400 hover:text-white">
              <Github class="h-5 w-5" />
            </a>
            <a href="#" class="text-gray-400 hover:text-white">
              <Twitter class="h-5 w-5" />
            </a>
            <a href="#" class="text-gray-400 hover:text-white">
              <Mail class="h-5 w-5" />
            </a>
          </div>
        </div>
        <div class="mt-8 text-center text-gray-400 text-sm">
          <p>© {{ new Date().getFullYear() }} Jonny Åhslund. All rights reserved.</p>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { Menu, X, ChevronDown, ExternalLink, Github, Mail, Linkedin, Twitter, MapPin } from 'lucide-vue-next';
import emailjs from 'emailjs-com';

// Mobile menu state
const mobileMenuOpen = ref(false);

// Experience data with accordion state
const experience = ref([
  {
    title: 'Senior Software Engineer',
    company: 'Tech Company',
    period: 'Jan 2021 - Present',
    description: 'Led the development of a complex web application that improved customer engagement by 40%.',
    responsibilities: [
      'Architected and implemented new features using Vue.js and Node.js',
      'Mentored junior developers and conducted code reviews',
      'Optimized application performance, reducing load time by 30%',
      'Collaborated with product managers to define and prioritize features'
    ],
    technologies: ['Vue.js', 'Node.js', 'TypeScript', 'MongoDB', 'Docker'],
    isOpen: false
  },
  {
    title: 'Software Developer',
    company: 'Digital Agency',
    period: 'Mar 2018 - Dec 2020',
    description: 'Worked on multiple client projects, delivering high-quality web applications on time and within budget.',
    responsibilities: [
      'Developed responsive web applications using React and Vue.js',
      'Implemented RESTful APIs using Express.js',
      'Collaborated with designers to implement pixel-perfect UI',
      'Participated in agile development processes'
    ],
    technologies: ['React', 'Vue.js', 'Express.js', 'PostgreSQL', 'AWS'],
    isOpen: false
  },
  {
    title: 'Junior Web Developer',
    company: 'Startup Inc.',
    period: 'Jun 2016 - Feb 2018',
    description: 'Contributed to the development of the company\'s main product, a SaaS platform for project management.',
    responsibilities: [
      'Built and maintained frontend components using Angular',
      'Implemented responsive designs and ensured cross-browser compatibility',
      'Fixed bugs and improved application performance',
      'Participated in daily stand-ups and sprint planning'
    ],
    technologies: ['Angular', 'JavaScript', 'CSS', 'HTML', 'Git'],
    isOpen: false
  }
]);

// Toggle accordion
const toggleAccordion = (index) => {
  experience.value[index].isOpen = !experience.value[index].isOpen;
};

// Projects data
const projects = ref([
  {
    title: 'E-commerce Platform',
    description: 'A full-stack e-commerce platform with product management, cart functionality, and payment processing.',
    image: 'https://via.placeholder.com/600x400',
    technologies: ['Vue.js', 'Node.js', 'Express', 'MongoDB', 'Stripe API'],
    demo: 'https://example.com/demo1',
    github: 'https://github.com/yourusername/project1'
  },
  {
    title: 'Task Management App',
    description: 'A responsive task management application with drag-and-drop functionality and real-time updates.',
    image: 'https://via.placeholder.com/600x400',
    technologies: ['React', 'Firebase', 'Material-UI', 'Redux'],
    demo: 'https://example.com/demo2',
    github: 'https://github.com/yourusername/project2'
  },
  {
    title: 'Weather Dashboard',
    description: 'A weather dashboard that displays current and forecasted weather data for multiple locations.',
    image: 'https://via.placeholder.com/600x400',
    technologies: ['JavaScript', 'HTML', 'CSS', 'Weather API', 'Chart.js'],
    demo: 'https://example.com/demo3',
    github: 'https://github.com/yourusername/project3'
  }
]);

// Contact form
const contactForm = ref({
  name: '',
  subject: '',
  email: '',
  message: ''
});

const submitForm = () => {
  emailjs
    .send(
      'service_bbd0s0d', 
      'your_template_id', 
      {
        name: contactForm.value.name,
        email: contactForm.value.email,
        message: contactForm.value.message,
      },
      'your_public_key' // This is your User ID from EmailJS
    )
    .then(() => {
      alert('Email sent successfully!');
      contactForm.value = { name: '', subject: '', email: '', message: '' };
    })
    .catch((error) => {
      console.error('Error sending email:', error);
      alert('Failed to send email.');
    });
};

// old 
// // Form submission
// const submitForm = () => {
//   // Here you would typically send the form data to your backend or email service
//   console.log('Form submitted:', contactForm.value);
//   alert('Thank you for your message! I will get back to you soon.');
//   // Reset form
//   contactForm.value = {
//     name: '',
//     email: '',
//     message: ''
//   };
// };
</script>

<style>
@import "tailwindcss";
html {
  scroll-behavior: smooth;
}
</style>