<script setup lang="ts">
// --- Imports ---
import { ref, computed } from 'vue'

// --- État réactif ---
// le nombre d'articles dans le panier
const nombreArticles = ref(0)

// le prix unitaire d'un article (en GNF)
const prixUnitaire = ref(25000)

// --- Valeurs dérivées ---
// le total, dérivé des deux refs (se recalcule automatiquement)
const totalPanier = computed(() => nombreArticles.value * prixUnitaire.value)
// le panier est vide si le nombre d'articles est égal à zéro
const panierVide = computed(() => nombreArticles.value === 0)

// --- Fonctions ---
// ajoute un article au panier
function ajouterArticle() {
  nombreArticles.value++
}
// fonction pour retirer un article du panier
function decrementerArticle() {
  if (nombreArticles.value > 0) {
    nombreArticles.value--
  } else {
    alert('Le panier est déjà vide !')
  }
}
</script>

<template>
  <!-- Bannière principale de la boutique -->
  <header>
    <div>
      <h1>🛒 Tanou Market</h1>
      <p>La boutique du quartier</p>
    </div>

    <div class="panier">
      <button @click="ajouterArticle">+ Ajouter un article</button>
      <button @click="decrementerArticle">- Retirer un article</button>
      <span class="badge">🛍️ {{ nombreArticles }} article(s)</span>
      <span class="total">{{ totalPanier }} GNF</span>
      <span>{{ panierVide }}</span>
    </div>
  </header>
</template>

<style scoped>
/* le scoped limite ces styles aux éléments de CE composant */
header {
  background-color: #42b883;
  color: white;
  padding: 16px 24px;
  display: flex;
  justify-content: space-between;
  align-items: center;
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

.panier {
  display: flex;
  align-items: center;
  gap: 12px;
}

.badge {
  background: white;
  color: #42b883;
  padding: 4px 10px;
  border-radius: 12px;
  font-weight: bold;
}

.total {
  font-weight: bold;
}

button {
  cursor: pointer;
  border: none;
  padding: 8px 12px;
  border-radius: 6px;
}
</style>
