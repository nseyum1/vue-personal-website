<template>
    <section>
      <h2>Contact Me</h2>
      <form @submit.prevent="submitForm">
        <div>
          <label for="name">Name:</label>
          <input id="name" v-model="contact.name" type="text" />
        </div>
        <div>
          <label for="email">Email:</label>
          <input id="email" v-model="contact.email" type="email" />
        </div>
        <button type="submit">Send</button>
      </form>
    </section>
  </template>
  
  <script>
  import { ref, watch, onMounted } from 'vue';
  
  export default {
    name: 'ContactSection',
    setup() {
      const contact = ref({ name: '', email: '' });
  
      // Bonus: Retrieve stored contact info from localStorage on component mount
      onMounted(() => {
        const storedContact = localStorage.getItem('contactSubmission');
        if (storedContact) {
          contact.value = JSON.parse(storedContact);
        }
      });
  
      // Watch for changes in the contact form and log them
      watch(
        contact,
        (newVal) => {
          console.log('Contact form changed:', newVal);
        },
        { deep: true }
      );
  
      // Submit the form and store the data in localStorage
      const submitForm = () => {
        console.log('Form submitted:', contact.value);
        localStorage.setItem('contactSubmission', JSON.stringify(contact.value));
        // Optionally, clear the form after submission
        // contact.value = { name: '', email: '' }
      };
  
      return { contact, submitForm };
    }
  };
  </script>
  
  <style scoped>
  section {
    padding: 20px;
  }
  form {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
  </style>
  