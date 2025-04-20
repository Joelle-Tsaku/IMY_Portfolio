<!-- Joelle Tsaku, u24984362 -->

<template>
    <div class="page">
      <div class="navbar-container">
        <img src="/public/Penguin.ico" alt="logo" class="logo"/>
        <h2>Information and Knowledge Systems Student</h2>
        <nav class="navbar">
          <NuxtLink to="/" class="nav-button">Home</NuxtLink>
          <NuxtLink to="/projects" class="nav-button">Projects</NuxtLink>
          <NuxtLink to="/contact" class="nav-button">Contact</NuxtLink>
        </nav>
      </div>
      
        <div class="content">
            <h1>My Projects</h1>
            <p class="intro">Explore some of the projects I have worked on during my academic journey.</p>
            
            <div class="projects">
                <div class="card">
                    <h3>Project 1: Module Bulletin Board</h3>
                    <p>A C# application requiring student login to access academic module announcements and course information.</p>
                </div>
                
                <div class="card">
                    <h3>Project 2: Typing game</h3>
                    <p>A beginner-friendly typing game built in C#. Players race against time to type the given words correctly and earn points.</p>
                </div>
                
                <div class="card">
                    <h3>Project 3: Music Playlist</h3>
                    <p>A platform that allows users to create, manage, and explore music playlists using Vue.js.</p>
                </div>

                <div class="card">
                    <h3>Project 4: Guessing Game</h3>
                    <p>A simple C++ console game where the player must guess Higher or Lower, depending on which country's populations are given.</p>
                </div>
            </div>
        </div>

        <footer>
            <p>&copy; 2025 - Joelle Tsaku</p>
        </footer>
    </div>
  </template>
  
<script setup>
useHead({
  title: 'Projects - Personal Portfolio',
});
</script>
  
<style scoped>
.content {
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
}

h1 {
    font-size: 2.5em;
    margin-bottom: 10px;
}

.intro {
    font-size: 1.2em;
    color: #bbb;
    margin-bottom: 30px;
}

.projects {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 20px;
}

.card {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  padding: 20px;
  border-radius: 12px;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  box-shadow: 0 4px 12px rgba(144, 92, 240, 0.3);
}

.card:hover {
    transform: translateY(-10px);
    box-shadow: 0 6px 20px rgba(97, 40, 202, 0.3);
}

.card h3 {
    font-size: 1.6em;
    margin-bottom: 10px;
    color: #9d91ff;
}

.card p {
    font-size: 1.1em;
    color: #ccc;
    }
</style>
  