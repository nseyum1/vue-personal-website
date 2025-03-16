<template>
  <div id="app">
    <nav>
      <button @click="activeSection = 'home'">Home</button>
      <button @click="activeSection = 'projects'">Projects</button>
      <button @click="activeSection = 'contact'">Contact</button>
    </nav>
    <!-- Transition for smooth section changes -->
    <transition name="fade" mode="out-in">
      <component :is="currentComponent" :key="activeSection" />
    </transition>
  </div>
</template>

<script>
import HomeSection from './components/HomeSection.vue';
import ProjectsSection from './components/ProjectsSection.vue';
import ContactSection from './components/ContactSection.vue';

export default {
  name: 'App',
  data() {
    return {
      activeSection: 'home'
    };
  },
  computed: {
    currentComponent() {
      if (this.activeSection === 'home') return HomeSection;
      else if (this.activeSection === 'projects') return ProjectsSection;
      else if (this.activeSection === 'contact') return ContactSection;
      return HomeSection;
    }
  }
};
</script>

<style>
/* Basic fade transition */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}
nav {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}
</style>
