<script setup>
defineProps({
  city: String,
  current: Object,
  days: Array
});
</script>

<template>
  <div class="text-center mb-3">
    <h2>{{ city }}</h2>
    <p>{{ current.condition }} — {{ current.tmp }}°C</p>
    <img :src="current.icon" alt="icone météo" width="64" height="64" />
  </div>

  <section class="row g-3">
    <div v-for="j in days" :key="j.day_long" class="col-12 col-md-4">
      <div class="card p-3 text-center">
        <h5>{{ j.day_long }}</h5>
        <img :src="j.icon" :alt="j.condition" width="64" height="64" />
        <p>{{ j.tmin }}°C / {{ j.tmax }}°C</p>
        <p class="text-muted">{{ j.condition }}</p>
      </div>
    </div>
  </section>
</template>
