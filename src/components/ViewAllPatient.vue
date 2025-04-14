<script setup>
import search from './search.vue'
import Patient from './Patient.vue'
import axios from 'axios';
import { ref } from 'vue'

const patients= ref([])
const filteredPatients= ref([])
axios.get('http://localhost:3000/')
  .then(response => {
    console.log("patients fetched successfully");
    patients.value=response.data;
    filteredPatients.value=response.data;
    console.log(patients.value);
  })
  .catch(error => {
    console.error('Error fetching patients:', error);
  });
const filter = function(filter) {
console.log("filtering patients");
  filteredPatients.value=patients.value.filter((patient) => {
  if (filter.name)
    if (!(patient.first_name + patient.last_name).toLowerCase().includes(filter.name.toLowerCase()))
      return false;
  if (filter.min_date)
    if (new Date(patient.date_of_birth)< new Date(filter.min_date))
      return false;
  if (filter.max_date)
    if (new Date(patient.date_of_birth) > new Date(filter.max_date))
      return false;
  if (filter.gender)
    if (filter.gender!=patient.gender)
      return false;
  if (filter.contact)
    if (filter.contact!=patient.contact)
      return false;
  if (filter.condition)
    if (!filter.condition.toLowerCase().includes(patient.condition.toLowerCase()))
      return false;
  return true;
  })
}
</script>
<template>
    <h2>View All patients</h2>
      <search @filter="filter"/>
    <div id="patients">
        <ul>
            <li v-for="patient in filteredPatients">
            <Patient v-bind="patient"/>
            </li>
        </ul>
    </div>
</template>
<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}

#patients {
  width:370px;
  margin: auto;
}
</style>
