<script setup lang="ts">
import { ref, computed } from 'vue'
interface Produit {
  id: number
  nom: string
  prix: number
  stock: number
}
const produits = ref<Produit[]>([
  { id: 1, nom: 'Produit A', prix: 10000, stock: 5 },
  { id: 2, nom: 'Produit B', prix: 15000, stock: 3 },
  { id: 3, nom: 'Produit C', prix: 20000, stock: 0 },
])
const rechercher = ref('')
const produitsFiltres = computed(() =>
  produits.value.filter((produit) =>
    produit.nom.toLowerCase().includes(rechercher.value.toLowerCase()),
  ),
)
</script>

<template>
  <section>
    <h2>Liste des produits</h2>
    <input v-model="rechercher" placeholder="Rechercher un produit..." />

    <p v-if="produitsFiltres.length === 0">Aucun produit trouvé 😕</p>

    <ul v-else>
      <li v-for="produit in produitsFiltres" :key="produit.id">
        <strong>{{ produit.nom }}</strong>
        <span>{{ produit.prix }} GNF</span>
        <span :class="{ rupture: produit.stock === 0 }">
          {{ produit.stock > 0 ? `Stock : ${produit.stock}` : 'Rupture' }}
        </span>
      </li>
    </ul>
  </section>
</template>

<style scoped>
section {
  padding: 24px;
}

input {
  width: 100%;
  max-width: 400px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 6px;
  margin-bottom: 16px;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  gap: 16px;
  padding: 12px;
  border-bottom: 1px solid #eee;
}

.rupture {
  color: #e74c3c;
  font-weight: bold;
}
</style>
