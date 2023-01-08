<template>
  <div
    class="input-group mb-3">
    <input
      class="InputFirstName"
      v-model="FirstName"
      placeholder="Vorname"
      @input="event => text = event.target.value">
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
  </div>

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
