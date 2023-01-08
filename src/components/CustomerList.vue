<template>

  <div>Selected: {{ selected }}</div>
  <div class="dropdown">
  <select v-model="selected" class="btn btn-secondary dropdown-toggle" type="button" data-bs-toggle="dropdown">

    <option v-if="!selected" disabled value="" class="dropdown-item">Kunden auswählen</option>
    <option v-for="Customer in data" :key="Customer.id" class="dropdown-item"> {{ Customer.firstName }} {{ Customer.lastName }}</option>
  </select>
  </div>



  <form @submit="saveCustomer()" v-if="!selected" class="row g-3 needs validation">
    <div class="col-md-4">
      <label for="validationServer01" class="form-label">Vorname</label>
      <input type="text" class="form-control is-valid" id="validationServer01" v-model="FirstName" required>
      <div class="valid-feedback">
        Das passt!
      </div>
    </div>
    <div class="col-md-4">
      <label for="validationServer02" class="form-label">Nachname</label>
      <input type="text" class="form-control is-valid" id="validationServer02" v-model="LastName" required>
      <div class="valid-feedback">
        Das passt!
      </div>
    </div>
    <div class="col-md-6">
      <label for="validationServer03" class="form-label">Adresse</label>
      <input type="text" class="form-control is-invalid" id="validationServer03" v-model="Address" required
             placeholder="Straße + Hausnr.">
      <div id="validationServer03Feedback" class="invalid-feedback">
        Das passt!
      </div>
    </div>
    <div class="col-md-3">
      <label for="validationServer05" class="form-label">Bundesland</label>
      <input type="text" class="form-control is-invalid" id="validationServer04" v-model="State" required>
      <div class="valid-feedback">
        Das passt!
      </div>
    </div>
    <div class="col-md-3">
      <label for="validationServer05" class="form-label">Geburtstag</label>
      <input type="text" class="form-control is-invalid" id="validationServer05" v-model="Birthday"
             placeholder="Format: JJJJ-MM-TT">
    </div>
    <div class="col-12">
      <button class="btn btn-primary" type="submit">Kunden anlegen</button>
      <button class="btn btn-primary" type="submit">Kunden löschen</button>
    </div>
  </form>

<!--  {{data}}-->

</template>


<script setup>
import {ref} from 'vue'


  const selected = ref()
  const data = ref(null)
  const error = ref(null)
  const FirstName = ref()
  const LastName = ref()
  const Address = ref()
  const State = ref()
  const Birthday = ref()

  //computed(() => {return data.value[1]})

/*  const FirstNameSelected =*/


  fetch('http://localhost:8080/api/v1/customer')
    .then((res) => res.json())
    .then((json) => (data.value = json))
    .catch((err) => (error.value = err))


  async function saveCustomer() {
    const myHeaders = new Headers();
    myHeaders.append("Content-Type", "application/json");

    const raw = JSON.stringify({
      firstName: FirstName.value,
      lastName: LastName.value,
      address: Address.value,
      state: State.value,
      birthday: Birthday.value
    });

    const requestOptions = {
      method: 'POST',
      headers: myHeaders,
      body: raw,
      redirect: 'follow'
    };

    await fetch("http://localhost:8080/api/v1/customer", requestOptions)
      .then((res) => res.text())
      .then(res => console.log(res))
      .catch(err => console.log('error', err));
  }

</script>


<style scoped>

</style>
