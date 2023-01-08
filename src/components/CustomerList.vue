<template>

  <div class="dropdown">
  <select v-model="selected" class="btn btn-secondary dropdown-toggle" type="button" data-bs-toggle="dropdown" aria-expanded="false">
    <option v-if="!selected" disabled value="" class="dropdown-item">Kunden auswählen</option>
    <option v-for="Customer in data" :key="Customer.id" class="dropdown-item">  {{ Customer.firstName }} {{ Customer.lastName }}</option>
  </select>
  </div>
<!--
Ich habe hier versucht, auf das einzelne Element aus selected zuzugreifen.
Das hat jedoch nicht geklappt, selbst wenn ich selected.id auswählen wollte.
Das habe ich aber benötigt, um mir die Daten des ausgewählten Kunden anzeigen zu lassen.
Hätte ich das geschafft, hätte ich an den Kundenstammdaten noch Änderungen vornehmen und diese speichern können
und einen spezifischen Kunden sogar komplett löschen können-->
<!--  <div>
   <p> {{selectedCustomer()}}</p>
  </div>-->

  <form @submit="saveCustomer()" v-if="!selected" class="row g-3 needs validation">
    <div class="col-md-4">
      <label for="validationServer05" class="form-label">Vorname</label>
      <input type="text" class="form-control is-invalid" id="validationServer05" v-model="FirstName" required>
      <div class="valid-feedback">
      </div>
    </div>
    <div class="col-md-4">
      <label for="validationServer05" class="form-label">Bundesland</label>
      <input type="text" class="form-control is-invalid" id="validationServer05" v-model="LastName" required>
      <div class="valid-feedback">
      </div>
    </div>
    <div class="col-md-6">
      <label for="validationServer05" class="form-label">Adresse</label>
      <input type="text" class="form-control is-invalid" id="validationServer03" v-model="Address" required
             placeholder="Straße + Hausnr.">
      <div id="validationServer03Feedback" class="invalid-feedback">
      </div>
    </div>
    <div class="col-md-3">
      <label for="validationServer05" class="form-label">Bundesland</label>
      <input type="text" class="form-control is-invalid" id="validationServer05" v-model="State" required>
      <div class="valid-feedback">
      </div>
    </div>
    <div class="col-md-3">
      <label for="validationServer05" class="form-label">Geburtstag</label>
      <input type="text" class="form-control is-invalid" id="validationServer05" v-model="Birthday"
             placeholder="Format: JJJJ-MM-TT">
    </div>
    <div class="col-12">
      <button class="btn btn-primary m-2" type="submit">Kunden anlegen</button> <!--m = margin (Abstand zwischen Buttons)-->
    </div>
  </form>

  <div> <button class="btn btn-danger m-2" @click="deleteCustomer()" type="button">Kunden löschen</button></div>

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

  /*const test = ref(selected.value.id);*/

  //computed(() => {return data.value[1]})

/*  const FirstNameSelected =*/

/**/
/*function selectedCustomer ()  {
  console.log(this.selected.key)
  console.log(this.data.find(customer => customer.id === 3))
    return this.selected ? this.data.find(customer => customer.id === this.selected.at(1)) : null
  }*/


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

  async function deleteCustomer() {
    const requestOptions = {
      method: 'DELETE',
      redirect: 'follow'
    };

    fetch("http://localhost:8080/api/v1/customer/12", requestOptions)
      .then(response => response.text())
      .then(result => console.log(result))
      .catch(error => console.log('error', error));
  }

</script>


<style scoped>

</style>
