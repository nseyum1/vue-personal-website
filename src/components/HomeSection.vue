<template>
    <section>
      <h1>Welcome to My Personal Website</h1>
      <!-- Conditionally display welcome message using v-if -->
      <p v-if="showMessage">Hello, I'm Naol Seyum. Welcome to my personal site!</p>
      <button @click="toggleMessage">
        {{ showMessage ? 'Hide Info' : 'Show Info' }}
      </button>
      <!-- Include the counter component -->
      <Counter />
    </section>
  </template>
  
  <script>
  import { ref } from 'vue';
  import Counter from './Counter.vue';
  
  export default {
    name: 'HomeSection',
    components: {
      Counter
    },
    setup() {
      const showMessage = ref(true);
      const toggleMessage = () => {
        showMessage.value = !showMessage.value;
      };
      return { showMessage, toggleMessage };
    }
  };
  </script>
  
  <style scoped>
  section {
    padding: 20px;
  }
  </style>
  