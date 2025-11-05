<template>
<h1>Météo Gironde</h1>
    
  <nav class="navbar navbar-expand navbar-dark bg-dark">
    <div class="container">
      <router-link class="navbar-brand" to="/">Météo Gironde</router-link>
      <ul class="navbar-nav ms-auto">
        
        <li class="nav-item">
          <router-link class="nav-link" to="/a-propos">À propos</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" to="/mentions-legales">Mentions légales</router-link>
        </li>
      </ul>
    </div>
  </nav>

  <router-view />
</template>
<script setup>
</script>
