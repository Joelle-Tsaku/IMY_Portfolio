<template>
  <div class="page">
    <div class="navbar-container">
      <img src="/public/Penguin.ico" alt="logo" class="logo"/>
      <h2> Information and Knowledge Systems Student </h2>
      <nav class="navbar">
        <NuxtLink to="/" class="nav-button">Home</NuxtLink>
        <NuxtLink to="/projects" class="nav-button">Projects</NuxtLink>
        <NuxtLink to="/contact" class="nav-button">Contact</NuxtLink>
      </nav>
    </div>

    <div class="me">
      <div class="content">
        <div class="photo"> 
          <br><img src="/public/Me3.jpg">
        </div>

        <div class="bio">
          <h1> Hi, I'm Joelle Tsaku </h1>
          <p> 
            I'm a second year Information and Knowledge Systems student at UP.
            I'm passionate about almost anything creativity-driven. I love learning new skills and exploring new ideas that make the digital world a little more fun!
          </p>
        </div>
      </div>

      <div class="action-buttons">
        <NuxtLink to="/projects" class="custom-button">View Projects</NuxtLink>
        <NuxtLink to="/contact" class="custom-button outline">Contact Me</NuxtLink>
      </div>
    </div>

    <!-- Joke and Weather Sections in a flex container -->
    <div class="info-sections">
      <!-- Joke Section -->
      <div class="joke"> 
        <h2>Would you like to hear a joke?</h2>
        <p>{{ joke.setup }}</p>
        <p><em>{{ joke.punchline }}</em></p>
        <button @click="getJoke" class="jokeBtn">Get Another Joke</button>
      </div>

      <!-- Weather Section -->
      <div class="weather">
        <h2>🌤️ Weather in Pretoria</h2>

        <!-- Error Handling -->
        <div v-if="error">
          <p style="color: red;">❌ {{ error }}</p>
        </div>

        <!-- Weather Data -->
        <div v-else-if="weather">
          <p><strong>Temperature:</strong> {{ weather.temperature }}</p>
          <p><strong>Wind:</strong> {{ weather.wind }}</p>
          <p><strong>Description:</strong> {{ weather.description }}</p>
        </div>
        <!-- Loading State -->
        <div v-else>
          <p>Loading weather data...</p>
        </div>
      </div>
    </div>

    <!-- Footer Section -->
    <footer>
      <p> 
        &copy; 2025 - Joelle Tsaku
      </p>
    </footer>
  </div>
</template>

<script setup>
useHead({
  title: 'Personal Portfolio',
});

import { ref, onMounted } from 'vue';

// Joke API setup
const joke = ref({ setup: '', punchline: '' });

async function getJoke() {
  try {
    const res = await fetch('https://official-joke-api.appspot.com/random_joke');
    const data = await res.json();
    joke.value = data;
  } catch (error) {
    joke.value.setup = 'Oops!';
    joke.value.punchline = 'Could not fetch a joke.';
  }
}

onMounted(() => {
  getJoke();
});

// Weather API setup
const weather = ref(null);
const error = ref(null);

onMounted(async () => {
  try {
    const res = await fetch('http://goweather.xyz/weather/Pretoria');
    if (!res.ok) throw new Error('Failed to fetch weather data.');
    weather.value = await res.json();
  } catch (err) {
    error.value = err.message;
  }
});
</script>

<style>
/* Styling remains the same */
.navbar-container {
  display: flex;
  align-items: center;
  justify-content: space-between;  
  border-radius: 10px;
  background-color: #1b1b1b;
  padding: 10px;
}

.navbar {
  display: flex;
  gap: 10px;
  margin-left: auto;
}

footer {
  text-align: center;
  background-color: #1b1b1b;
  margin-top: auto;
  color: #999; 
  border-radius: 10px;
}

footer p {
  padding-left: 20px;
}

.nav-button {
  color: white;
  background-color: #555; 
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  text-decoration: none;
  font-weight: bold;
  cursor: pointer;
  transition: background-color 0.2s;
}

.nav-button:hover {
  background-color: #777;
  color: #c57ec2;
}

.page {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

body {
  background-color: black;
  color: white;
  background-image: url('Background.png');
}

.bio {
  color: white;
  display: flex;
  flex-direction: column;
  justify-content: center;
  max-width: 400px;
}

.bio h1 {
  font-size: 2.5em;
  font-weight: 700;
  margin-bottom: auto;
  color: #c57ec2; /* Soft purple */
  text-shadow: 1px 1px 5px rgba(197, 126, 194, 0.3);
}

.bio p {
  font-size: 1.1em;
  line-height: 1.6;
  color: #e0e0e0;
  padding: 20px;
  margin-top: auto;
}

.logo {
  width: 50px; 
  height: 50px;
  margin-right: 20px;
  cursor: pointer;
}

.content {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  margin: 80px 300px;
  gap: 100px;
  margin-bottom: auto;
}

.me {
  margin-bottom: 40px;
}

.photo img {
  width: 400px;
  height: 400px;
  border-radius: 15px;
  box-shadow: 0 10px 25px rgba(167, 99, 187, 0.4);
}

h2 {
  margin: 0;
  color: white; 
  font-size: 1.2em;
}

.action-buttons {
  display: flex;
  gap: 20px;
  justify-content: center;
  margin-left: 190px;
  margin-top: -80px;
}

.custom-button {
  padding: 12px 24px;
  border-radius: 8px;
  background-color: #8e44ad; /* deep purple */
  color: white;
  font-weight: bold;
  text-decoration: none;
  transition: all 0.3s ease;
}

.custom-button:hover {
  background-color: #a569bd;
  box-shadow: 0 0 12px #a569bd;
}

.custom-button.outline {
  background-color: transparent;
  border: 2px solid #8e44ad;
  color: #8e44ad;
}

.custom-button.outline:hover {
  background-color: #8e44ad;
  color: white;
  box-shadow: 0 0 12px #8e44ad;
}

.joke {
  position: fixed;
  top: 150px; /* adjust as needed */
  right: 20px;
  width: 300px;
  padding: 20px;
  background-color: #2a2a2a;
  border-radius: 10px;
  box-shadow: 0 0 15px rgba(130, 85, 165, 0.3);
  z-index: 1000;
  text-align: center;
}

.joke p {
  color: #e0e0e0;
  font-size: 1.2em;
}

.jokeBtn {
  margin-top: 15px;
  padding: 10px 20px;
  background-color: #8e44ad;
  color: white;
  border: none;
  border-radius: 6px;
  font-weight: bold;
  cursor: pointer;
  transition: background-color 0.3s, box-shadow 0.3s;
}

.jokeBtn:hover {
  background-color: #a569bd;
  box-shadow: 0 0 10px #a569bd;
}

.weather {
  margin-top: 40px;
  margin-right: 20px;
  background-color: #1e1e1e;
  color: #fff;
  padding: 25px;
  border-radius: 10px;
  box-shadow: 0 0 8px rgba(255, 255, 255, 0.1);
}



.info-sections {
  display: flex;
  justify-content: right;
  margin-top: -60px;
  padding-right: 20px; /* leave room for the fixed joke box */
}
</style>
