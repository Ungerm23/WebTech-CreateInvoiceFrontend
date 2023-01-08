<template>
  <div class="dropdown">
    <button class="btn btn-secondary dropdown-toggle" type="button" data-bs-toggle="dropdown" aria-expanded="false">
      Artikel auswählen
    </button>
    <ul class="dropdown-menu">
      <li><a  v-for="Article in data" :key="Article.id" class="dropdown-item"
              href="#">{{ Article.articleName }} {{ Article.price }}</a></li>
    </ul>
  </div>

  <div v-for="Article in Articles" :key="Article.id">
    <p>
      {{ Article.articleName }}
    </p>
    <p>
      {{ Article.price }}
    </p>
  </div>

  <div> <button class="btn btn-primary m-2" type="button">Artikel hinzufügen</button></div>

</template>


<script setup>
  import {ref} from 'vue'

  const data = ref(null)
  const error = ref(null)

  fetch('http://localhost:8080/api/v1/article')
    .then((res) => res.json())
    .then((json) => (data.value = json), console.log(data))
    .catch((err) => (error.value = err))


</script>

<style scoped>

</style>
