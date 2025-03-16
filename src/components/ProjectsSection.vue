<template>
    <section>
      <h2>Projects</h2>
      
      <p v-if="projects.length === 0">No projects available</p>
      <ul v-else>
        <li v-for="(project, index) in projects" :key="index">{{ project }}</li>
      </ul>
      
      <p>Total Projects: {{ projectCount }}</p>
    </section>
  </template>
  
  <script>
  import { ref, computed } from 'vue';
  
  export default {
    name: 'ProjectsSection',
    setup() {

      const projects = ref(['Vue assignment 1', 'Vue assignment 2', 'Personal Website']);

      const projectCount = computed(() => projects.value.length);
      return { projects, projectCount };
    }
  };
  </script>
  
  <style scoped>
  section {
    padding: 20px;
  }
  </style>
  