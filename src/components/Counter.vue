<template>
    <div>
      <button @click="incrementCounter">Click Me</button>
      <p>Counter: {{ counter }}</p>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  
  export default {
    name: 'Counter',
    setup() {
      const counter = ref(0);
      const incrementCounter = () => {
        counter.value++;
      };
      return { counter, incrementCounter };
    }
  };
  </script>
  
  <style scoped>
  div {
    margin-top: 20px;
  }
  </style>
  