<!-- Le squelette de base d'un composant Vue 3 avec TypeScript et le style scoped -->
<!-- le scoped sert a limiter l'application des styles aux éléments du composant -->
<script setup lang="ts"></script>

<template>
  <header>
    <h1>🛒 Tanou Market</h1>
    <p>La boutique du quartier</p>
  </header>
</template>

<style scoped>
header {
  background-color: #42b883;
  color: white;
  padding: 16px 24px;
}

h1 {
  margin: 0;
  font-size: 1.5rem;
}

p {
  margin: 4px 0 0;
  font-size: 0.9rem;
  opacity: 0.9;
}
</style>
