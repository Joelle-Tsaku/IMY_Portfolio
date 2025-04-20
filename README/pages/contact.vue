<!-- Joelle Tsaku, u24984362 -->

<template>
    <div class="page">
      <!-- Navbar -->
      <div class="navbar-container">
        <img src="/public/Penguin.ico" alt="logo" class="logo" NuxtLink to="/"/>
        <h2>Information and Knowledge Systems Student</h2>
        <nav class="navbar">
          <NuxtLink to="/" class="nav-button">Home</NuxtLink>
          <NuxtLink to="/projects" class="nav-button">Projects</NuxtLink>
          <NuxtLink to="/contact" class="nav-button">Contact</NuxtLink>
        </nav>
      </div>
  
      <div class="content-container">
        <h1 class="heading">Contact Me</h1>
  
        <form name="contact" method="POST" data-netlify="true" netlify action="/thanks">
            <input type="hidden" name="form-name" value="contact" />

            <label for="name">First Name</label>
            <input type="text" id="name" name="name" v-model="name" required />
    
            <label for="surname">Last Name</label>
            <input type="text" id="surname" name="surname" v-model="surname" required />
    
            <label for="email">Email</label>
            <input type="email" id="email" name="email" v-model="email" required />
    
            <label for="message">Message</label>
            <textarea id="message" name="message" v-model="message" placeholder="Chat with me" required></textarea>
    
            <button type="submit">Send</button>
        </form>
      </div>
  
      <footer>
        <p>&copy; 2025 - Joelle Tsaku</p>
      </footer>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  import { useHead } from '#imports'
  
  const name = ref('')
  const surname = ref('')
  const email = ref('')
  const message = ref('')
  
  useHead({
    title: 'Contact - Personal Portfolio',
  })
  
  function thanks() {
    alert(`Thank you, ${name.value}! Your message has been sent.`)
  }
  </script>
  
  <style scoped>
  .content-container {
    width: 700px;
    margin: 30px auto;
    align-items: center;
    background-color: #1c1c1c;
    padding: 30px;
    border-radius: 12px;
    box-shadow: 0 0 10px rgba(141, 122, 221, 0.6);
  }
  
  .heading {
  font-size: 2.5em;
  color: #9d91ff;
  text-align: center;
  margin: 40px 0 20px;
}

  h1 {
    text-align: center;
    font-size: 2.4em;
    margin-bottom: 30px;
  }
  
  form {
  display: flex;
  flex-direction: column;
}

label {
  margin: 15px 0 5px;
  font-weight: bold;
  color: #ccc;
}

input,
textarea {
  background-color: #2a2a2a;
  border: 1px solid #444;
  color: white;
  padding: 12px;
  border-radius: 6px;
  font-size: 1em;
  transition: border-color 0.2s;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #c57ec2;;
}

textarea {
  min-height: 120px;
}

button {
  margin-top: 20px;
  background-color: #c57ec2;
  color: white;
  padding: 12px;
  border: none;
  border-radius: 6px;
  font-size: 1em;
  font-weight: bold;
  cursor: pointer;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #a736a1;
}
  </style>
  