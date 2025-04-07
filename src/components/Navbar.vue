<template>
<nav class="bg-white shadow-sm dark:bg-gray-800 border-b border-gray-300">
    <div class="container mx-auto px-4 py-4 flex justify-between items-center">
        <div class="text-xl font-bold text-gray-800 dark:text-white">
            Jonny Åhslund - Age {{ currentAge }}
        </div>
        <div class="hidden md:flex space-x-6">
            <a href="#about" class="text-gray-600 hover:text-gray-900 dark:text-gray-300 dark:hover:text-white">About</a>
            <a href="#experience" class="text-gray-600 hover:text-gray-900 dark:text-gray-300 dark:hover:text-white">Experience</a>
            <a v-if="hasProjects" href="#projects" class="text-gray-600 hover:text-gray-900 dark:text-gray-300 dark:hover:text-white">Projects</a>
            <a href="#contact" class="text-gray-600 hover:text-gray-900 dark:text-gray-300 dark:hover:text-white">Contact</a>
        </div>
        <button @click="mobileMenuOpen = !mobileMenuOpen" class="md:hidden">
            <Menu v-if="!mobileMenuOpen" class="h-6 w-6 text-gray-600 dark:text-gray-300" />
            <X v-else class="h-6 w-6 text-gray-600 dark:text-gray-300" />
        </button>
    </div>
    <!-- Mobile menu -->
    <div v-if="mobileMenuOpen" class="md:hidden bg-white py-2 px-4 dark:bg-gray-800">
        <div class="flex flex-col space-y-3">
            <a href="#about" class="text-gray-600 hover:text-gray-900 dark:text-gray-300 dark:hover:text-white" @click="mobileMenuOpen = false">About</a>
            <a href="#experience" class="text-gray-600 hover:text-gray-900 dark:text-gray-300 dark:hover:text-white" @click="mobileMenuOpen = false">Experience</a>
            <a v-if="hasProjects" href="#projects" class="text-gray-600 hover:text-gray-900 dark:text-gray-300 dark:hover:text-white" @click="mobileMenuOpen = false">Projects</a>
            <a href="#contact" class="text-gray-600 hover:text-gray-900 dark:text-gray-300 dark:hover:text-white" @click="mobileMenuOpen = false">Contact</a>
        </div>
    </div>
    </nav>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const props = defineProps({
    hasProjects: Boolean
});

onMounted(() => {
  getCurrentAge();
});

const currentAge = ref("");
const mobileMenuOpen = ref(false);

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

</script>