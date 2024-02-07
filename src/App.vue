<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <h1>Test</h1>

    <nav class="*:text-red-500 flex flex-col">
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/maisons">Maison</RouterLink>
      <RouterLink to="/connexion">Connexion</RouterLink>
      <RouterLink to="/maisons/edit">Edit</RouterLink>
    </nav>
  </header>

  
  <Suspense>
    
    <RouterView />
  
  </Suspense>
</template>

<style>
  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
    background-color: #f3f3f3;
  }


  nav a {
    margin-right: 1rem;
  }

  nav a:hover {
    text-decoration: underline;
  }

  nav a.active {
    font-weight: bold;
  }

  nav a.active:hover {
    text-decoration: none;
  }

  .margin-auto {
    margin: auto;
  }

  .justify-center {
    justify-content: center;
  }

  .grid {
    display: grid;
  }


</style>