<template>
    <div class="thanks-page">
      <h1>Thank You!</h1>
      <p>Your message has been received. I’ll be in touch soon. 😊</p>
      <NuxtLink to="/" class="go-home">Back to Home</NuxtLink>
    </div>
  </template>
  
  <script setup>
  useHead({
    title: 'Thank You - Personal Portfolio',
  })
  </script>
  
  <style scoped>
  .thanks-page {
    text-align: center;
    padding: 60px 20px;
    color: #9d91ff;
  }
  .go-home {
    display: inline-block;
    margin-top: 30px;
    background-color: #c57ec2;
    padding: 10px 20px;
    border-radius: 6px;
    color: white;
    text-decoration: none;
    font-weight: bold;
  }
  .go-home:hover {
    background-color: #a736a1;
  }
  </style>
  