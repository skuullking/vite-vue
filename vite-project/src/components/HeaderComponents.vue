<template>
    <header>
      <h1>Mon Application</h1>
      <nav>
        <ul>
          <li><a href="#">Accueil</a></li>
          <li><a href="#">À Propos</a></li>
          <li><a href="#">Contact</a></li>
        </ul>
      </nav>
    </header>
  </template>
  
  <script setup lang="ts">
  </script>
  
  <style >
  header {
    background-color: #333;
    color: white;
    padding: 15px;
    text-align: center;
  }
  
  nav ul {
    list-style: none;
    padding: 0;
  }
  
  nav ul li {
    display: inline;
    margin: 0 10px;
  }
  
  nav ul li a {
    color: white;
    text-decoration: none;
  }
  </style>
  