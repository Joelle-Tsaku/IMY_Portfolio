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

    <slot />

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
</script>

<style>

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
display: block;
background-color: #1b1b1b;
margin-top: auto;
color: white; 
border-radius: 10px;
}
footer p {
padding-left: 20px;;
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
}

.page {
display: flex;
flex-direction: column;
min-height: 100vh;
}
body {
background-color: black;
}
</style>