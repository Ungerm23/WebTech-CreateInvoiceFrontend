<template>
  <form class="row g-3 needs validation" >
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
      <button class="btn btn-primary" type="submit">Submit form</button>
    </div>
  </form>

<!--  <div
    class="input-group mb-3">
    <input
      class="InputFirstName"
      v-model="FirstName"
      placeholder="Vorname"
      @input="event => text = event.target.value"
      >
    <p>{{FirstName}}</p>
  </div>

  <input
    class="input-group mb-3"
    v-model="LastName"
    placeholder="Nachname"
    @input="event => text = event.target.value">
  <p>{{LastName}}</p>

  <div
    class="input-group mb-3">
    <input
      class="InputAddress"
      v-model="Address"
      placeholder="Straße + Hausnr."
      @input="event => text = event.target.value">
    <p>{{Address}}</p>
  </div>

  <div
    class="input-group mb-3">
    <input
      class="InputState"
      v-model="State"
      placeholder="Bundesland"
      @input="event => text = event.target.value">
    <p>{{State}}</p>
  </div>

  <div
    class="input-group mb-3">
    <input
      class="InputBirthday"
      v-model="Birthday"
      placeholder="Geburtstag (JJJJ-MM-TT)"
      @input="event => text = event.target.value">
    <p>{{Birthday}}</p>
  </div>-->

</template>


<script setup>
  import {ref} from "vue";

  const FirstName = ref()
  const LastName = ref()
  const Address = ref()
  const State = ref()
  const Birthday = ref()

</script>


<style scoped>


.InputFirstName {
  background-color: darkgray;
}

input {
  background-color: cadetblue;
  font-family: Calibri;
}


</style>
