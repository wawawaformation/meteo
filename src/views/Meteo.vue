<script setup>
import { ref, onMounted } from "vue";
import { fetchMeteo } from "@/services/meteo.js";
import Resultat from "@/components/Resultat.vue";


const villes = [
  { code: "bordeaux", nom: "Bordeaux" },
  { code: "arcachon", nom: "Arcachon" },
  { code: "libourne", nom: "Libourne" },
  { code: "blaye", nom: "Blaye" },
  
];

const ville = ref("bordeaux");
const meteo = ref(null);
const loading = ref(false);
const error = ref("");

async function chargerMeteo() {
  error.value = "";
  loading.value = true;
  meteo.value = null;
  try {
    meteo.value = await fetchMeteo(ville.value);
  } catch (e) {
    error.value = e.message;
  } finally {
    loading.value = false;
  }
}

// ✅ Charger dès le montage du composant
onMounted(chargerMeteo);
</script>

<template>

  <div class="container py-4">

    <form class="d-flex flex-column align-items-center gap-2" @submit.prevent>
      <label for="ville" class="form-label">Choisir une ville :</label>
      <div class="d-flex gap-2">
        <select id="ville" v-model="ville" class="form-select w-auto" @change="chargerMeteo">
          <option v-for="v in villes" :key="v.code" :value="v.code">{{ v.nom }}</option>
        </select>
      </div>
    </form>

    <div class="mt-4">
      <div v-if="loading" class="alert alert-secondary">Chargement...</div>
      <div v-else-if="error" class="alert alert-danger">Erreur : {{ error }}</div>
      <Resultat
        v-else-if="meteo"
        :city="meteo.city"
        :current="meteo.current"
        :days="meteo.days"
      />
    </div>
  </div>

</template>
