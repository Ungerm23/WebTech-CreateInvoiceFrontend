<template>

  <div>Selected: {{ selected }}</div>
  <div class="dropdown">
  <select v-model="selected" class="btn btn-secondary dropdown-toggle" type="button" data-bs-toggle="dropdown">

    <option v-if="!selected" disabled value="" class="dropdown-item">Kunden auswählen</option>
    <option v-for="Customer in data" :key="Customer.id" class="dropdown-item"> {{ Customer.firstName }} {{ Customer.lastName }}</option>
  </select>
  </div>

</template>


<script setup>
  import {ref} from 'vue'

  const selected = ref()
  const data = ref(null)
  const error = ref(null)

  fetch('http://localhost:8080/api/v1/customer')
    .then((res) => res.json())
    .then((json) => (data.value = json))
    .catch((err) => (error.value = err))

</script>


<style scoped>

</style>
