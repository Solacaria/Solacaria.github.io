<template>
  <div class="min-h-screen bg-gray-50">
    <Navbar :hasProjects="hasProjects" class="border-b border-gray-500"/>
    <Hero :hasProjects="hasProjects" class="border-b border-gray-500"/>
    <Experience class="border-b border-gray-500"/>
    <Education class="border-b border-gray-500"/>
    <Project v-show="hasProjects" class="border-b border-gray-500"/>
    <Contact class="border-b border-gray-500"/>
    <Footer/>
  </div>
</template>

<script setup>
import Contact from './components/Contact.vue';
import Hero from './components/Hero.vue';
import Experience from './components/Experience.vue';
import Project from './components/Project.vue';
import Education from './components/Education.vue';
import Footer from './components/Footer.vue';
import Navbar from './components/Navbar.vue';

// Disables project section
const hasProjects = false;
</script>

<style>
@import "tailwindcss";
html {
  scroll-behavior: smooth;
}
</style>