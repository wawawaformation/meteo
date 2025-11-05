<template>
  <header id="header">
    <h1>Atmos</h1>
  </header>

<main id="main">
    <router-view />
</main>


  <footer>
    <nav>
      <ul class="menu main-menu">
        <li><router-link to="/">Météo</router-link></li>
        <li><router-link to="/a-propos">À propos</router-link></li>
        <li>
          <router-link to="/mentions-legales">Mentions légales</router-link>
        </li>
      </ul>
      <ul class="menu rs-menu">
        <li><a href="#">Facebook</a></li>
        <li><a href="#">Osef</a></li>
      </ul>
    </nav>
  </footer>
</template>
<script setup>
</script>