<script setup>
import { ref } from 'vue'
import Patient from './components/Patient.vue'
import AddPatient from './components/AddPatient.vue'
import axios from 'axios';

const patients= ref([])
axios.get('http://localhost:3000/')
  .then(response => {
    console.log(response.data);
    console.log("patients fetched successfully");
    patients.value=response.data;
    console.log(patients.value);
  })
  .catch(error => {
    console.error('Error fetching patients:', error);
  });
</script>

<template>
  <header>
    <h1>Patient Manager</h1>
  </header>
  <main>
    <AddPatient/>
    <div id="patients">
      <div id="title">
        <h2>View All patient</h2>
      </div>
      <ul>
        <li v-for="patient in patients">
          <Patient v-bind="patient"/>
        </li>
      </ul>
    </div>
  </main>
</template>

<style scoped>
header {
  background-color: var(--bg--color);
  border: 1px solid var(--border);
  border-radius: 8px;
  padding-left: 20px;
  position: fixed;
  width:100%;
}
main {
  height: 80%;
  display: flex;
  justify-content: center;
  top: 40px;
  #title{
    background-color: var(--bg--color);
    position: fixed;
    top:50px;
    left:calc(10% + 357px);
    font-size: 2rem;
    font-weight: bold;
    width:405px;
  }
  ul{
    padding-top:120px;
    list-style: none;
  }
  li{
    margin: 10px;
  }
  #add_patient{
    top: 50px;
    left: 10%;
    position:fixed;
  }
  #patients{
    float: right;
  }
}
/* @media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
} */
</style>
