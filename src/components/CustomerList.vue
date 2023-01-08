<template>

  <div class="dropdown">
    <button class="btn btn-secondary dropdown-toggle" type="button" data-bs-toggle="dropdown" aria-expanded="false">
      Dropdown button
    </button>
    <ul class="dropdown-menu">
      <li><a  v-for="Customer in data" :key="Customer.id" class="dropdown-item"
              href="#">{{ Customer.firstName }} {{ Customer.lastName }}</a></li>
    </ul>
  </div>

  <div v-for="Customer in data" :key="Customer.id">
    <p>
      {{ Customer.firstName }} {{ Customer.lastName }}
    </p>
  </div>


</template>


<script setup>
  import {ref} from 'vue'

/*  const Customers = [{
    id: 1,
    FirstName: "Mark",
    LastName: "Mustermann"
  },
    {
      id: 2,
      FirstName: "Max",
      LastName: "Meier"
    }
  ]*/

  const data = ref(null)
  const error = ref(null)

  fetch('http://localhost:8080/api/v1/customer')
    .then((res) => res.json())
    .then((json) => (data.value = json), console.log(data))
    .catch((err) => (error.value = err))

/*  {
    const requestOptions = {
      method: 'GET',
      redirect: 'follow'
    };

    fetch('http://localhost:8080/api/v1/customer', requestOptions)
      .then(response => response.json())
      .then(result => console.log(result))
      .catch(error => console.log('error', error))
  }*/

</script>


<style scoped>

</style>
