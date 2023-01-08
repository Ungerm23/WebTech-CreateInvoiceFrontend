<template>
  <h1>Welcome to Customers</h1>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Customers',
  data() {
    return {
      customers: []
    }
  },
  methods: {},
  mounted() {
    const requestOptions = {
      method: 'GET',
      redirect: 'follow'
    };

    fetch('http://localhost:8080/api/v1/customer', requestOptions)
      .then(response => response.json())
      .then(result => console.log(result))
      .catch(error => console.log('error', error))
  }
}

</script>

<style scoped>

</style>
