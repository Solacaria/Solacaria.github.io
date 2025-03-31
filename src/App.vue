<template>
  <div class="min-h-screen bg-gray-50">
    <!-- Navigation -->
    <nav class="bg-white shadow-sm">
      <div class="container mx-auto px-4 py-4 flex justify-between items-center">
        <div class="text-xl font-bold text-gray-800">Jonny Åhslund - Age {{ currentAge }}</div>
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
    <section id="about" class="py-16 md:py-24 bg-white bg-hero-colour" >
      <div class="container mx-auto px-4">
        <div class="flex flex-col md:flex-row items-center">
          <div class="md:w-1/2 mb-8 md:mb-0 m-4">
            <div class="relative w-64 h-64 mx-auto md:mx-0 rounded-full overflow-hidden border-4 border-gray-400">
              <img
                src="../src/assets/Selfiee.jpg"
                alt="Your Profile"
                class="w-full h-full object-cover"
              />
            </div>
          </div>
          <div class="md:w-1/2 md:pl-12">
            <h1 class="text-4xl md:text-5xl font-bold text-gray-800 mb-4">
              Hi, I'm <span class="text-emerald-600">Jonny</span>
            </h1>
            <h2 class="text-2xl text-gray-600 mb-6">A Junior Software Engineer</h2>
            <p class="text-gray-600 mb-8 leading-relaxed">
              Passionate about problem-solving and structured thinking, I thrive in environments that value efficiency and organization. <br><br>

              With experience in both logistics and transportation, 
              I have developed a keen eye for detail and a methodical approach to challenges—qualities that I also apply in my personal interests, 
              such as technology and strategic problem-solving.<br><br>

              I am motivated by creating intuitive and well-structured solutions, 
              always striving for a balance between simplicity and effectiveness. <br>
              
              I value teamwork and continuous learning, 
              and I am eager to contribute my skills in an environment that fosters collaboration and professional growth.
            </p>
            <div class="flex space-x-4">
              <a
                href="#contact"
                class="px-6 py-3 bg-emerald-600 text-white rounded-md hover:bg-emerald-700 transition-colors"
                style="color: inherit; text-decoration: none;"
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
              @click="toggleExpAccordion(index)"
              class="flex justify-between items-center p-4 bg-gray-200 rounded-md shadow-md cursor-pointer hover:bg-gray-50 transition-colors"
            >
              <div class="place-items-start">
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
              <p class="text-gray-600 mb-4 font-medium">{{ job.description }}</p>
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

    <!-- Education Section -->
    <section id="experience" class="py-16 md:py-24 bg-gray-50">
      <div class="container mx-auto px-4">
        <h2 class="text-3xl font-bold text-center mb-12 text-gray-800">Educations</h2>
        
        <div class="max-w-3xl mx-auto">
          <div v-for="(course, index) in education" :key="index" class="mb-4">
            <div
              @click="toggleEduAccordion(index)"
              class="flex justify-between items-center p-4 bg-gray-200 rounded-md shadow-md cursor-pointer hover:bg-gray-50 transition-colors"
            >
              <div class="place-items-start">
                <h3 class="font-semibold text-lg text-gray-800">{{ course.title }}</h3>
                <p class="text-gray-600"> {{ course.extraInfo }} | {{ course.period }}</p>
              </div>
              <ChevronDown
                :class="{ 'transform rotate-180': course.isOpen }"
                class="h-5 w-5 text-gray-500 transition-transform duration-200"
              />
            </div>
            <div
              v-if="course.isOpen"
              class="bg-white p-4 rounded-b-md shadow-sm border-t border-gray-100 mt-px"
            >
              <p class="text-gray-600 mb-4 font-medium">{{ course.description }}</p>
              <ul class="list-disc pl-5 space-y-2">
                <li v-for="(className, rIndex) in course.classes" :key="rIndex" class="text-gray-600">
                  {{ className }}
                </li>
              </ul>
              <div v-if="course.technologies" class="mt-4">
                <p class="font-medium text-gray-700 mb-2">Technologies:</p>
                <div class="flex flex-wrap gap-2">
                  <span
                    v-for="(tech, tIndex) in course.technologies"
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
    <section id="projects" class="py-16 md:py-24 bg-white" v-show="hasProjects">
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
          <div class="mb-4 md:mb-0 place-items-start">
            <p class="text-lg font-semibold">Jonny Åhslund</p>
            <p class="text-gray-400">Junior Software Engineer</p>
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
import { ref, onMounted } from 'vue';
import { Menu, X, ChevronDown, ExternalLink, Github, Mail, Linkedin, Twitter, MapPin } from 'lucide-vue-next';
import emailjs from 'emailjs-com';

onMounted(() => {
  getCurrentAge();
})
// Current age
const currentAge = ref(33);

const getCurrentAge = () => {
  const dob = new Date("1991-04-17");
  const now = new Date();

  let age = now.getFullYear() - dob.getFullYear();

  const hasBirthdayPassed = (now.getMonth() > dob.getMonth()) || 
                            (now.getMonth() === dob.getMonth() && now.getDate() >= dob.getDate());

  if (!hasBirthdayPassed) {
    age--;
  }
  currentAge.value = age;
}

// Mobile menu state
const mobileMenuOpen = ref(false);

// Disables project section
const hasProjects = true;

// Education data with accordion state
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

// Experience data with accordion state
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

// Toggle accordions
const toggleExpAccordion = (index) => {
  experience.value[index].isOpen = !experience.value[index].isOpen;
};
const toggleEduAccordion = (index) => {
  education.value[index].isOpen = !education.value[index].isOpen;
};

// Projects data
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
    description: 'Add, remove, edit and save recipes with ease. Has search function for tags and title',
    image: '../src/assets/test_image.png',
    technologies: ['MAUI', 'C#', 'XAML', ],
    demo: '',
    github: 'https://github.com/Solacaria/PP-MAUI-Cookbook-WIP'
  },
]);

// Contact form
const contactForm = ref({
  name: '',
  subject: '',
  email: '',
  message: '',
  time: '',
});

const submitForm = () => {
  emailjs
    .send(
      'service_bbd0s0d', //service id
      'template_25ofj5b', //template id
      {
        name: contactForm.value.name,
        email: contactForm.value.email,
        subject: contactForm.value.subject,
        message: contactForm.value.message,
        time: getCurrentTime(),
      },
      'TrcC2ljFtXS_-zFOE' //public key
    )
    .then(() => {
      alert('Email sent successfully!');
      contactForm.value = { name: '', subject: '', email: '', message: '', time: '' };
    })
    .catch((error) => {
      console.error('Error sending email:', error);
      alert('Failed to send email.');
    });
};

const getCurrentTime = () => {
  const now = new Date();
  const formattedTime = `${now.getFullYear()}/${String(now.getMonth() + 1).padStart(2, '0')}/${String(now.getDate()).padStart(2, '0')} - ${String(now.getHours()).padStart(2, '0')}:${String(now.getMinutes()).padStart(2, '0')}`;
  return formattedTime;
};

// old submitForm
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

.bg-hero-colour{
  background: linear-gradient(to right, #059669, #91b9fa);
  border-bottom: 2px black solid;
}
</style>