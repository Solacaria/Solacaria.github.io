<template>
    <section id="about" class="py-16 md:py-24 bg-white bg-gradient-to-r from-gray-500 to-gray-900 md:from-gray-300 md:to-gray-900" >
      <div class="container mx-auto px-4">
        <div class="flex flex-col md:flex-row items-center">
          <div class="md:w-1/2 mb-8 md:mb-0 m-4">
            <div class="relative w-64 h-64 mx-auto md:mx-0 rounded-full overflow-hidden border-4 border-gray-400">
              <img
                src="../../src/assets/Selfiee.jpg"
                alt="Your Profile"
                class="w-full h-full object-cover"
              />
            </div>
          </div>
          <div class="md:w-1/2 md:pl-12">
            <h1 class="text-4xl md:text-5xl font-bold text-gray-300 mb-4">
              Hi, I'm <span class="text-emerald-600">Jonny</span>
            </h1>
            <h2 class="text-2xl text-gray-300 mb-6">A Junior Software Engineer</h2>
            <p class="text-gray-300 mb-8 leading-relaxed">
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
                v-if="hasProjects"
                href="#projects"
                class="px-6 py-3 border border-gray-300 text-gray-700 rounded-md hover:bg-gray-400 transition-colors"
                >
                View Projects
                </a>
             
            </div>
          </div>
        </div>
      </div>
    </section>
</template>

<script setup>
  const props = defineProps({
    hasProjects: Boolean
  });

</script>