<script setup>
import { ref } from 'vue'
import AddPatient from './components/AddPatient.vue'
import search from './components/search.vue'
import Patient from './components/Patient.vue'
import axios from 'axios';
import { watch } from 'vue'
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
  <header>
    <h1>Patient Manager</h1>
  </header>
  <div class="flex-container">
    <div class="panel form-panel">
      <AddPatient />
    </div>
    <div class="panel list-panel">
      <h2>View All patients</h2>
      <search @filter="filter"/>
      <div id="patients">
        <ul>
          <li v-for="patient in filteredPatients">
            <Patient v-bind="patient"/>
          </li>
        </ul>
      </div>
    </div>
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
.flex-container {
  display: flex;
  height: calc(100vh - 48px);
  width: 100%;
  overflow: hidden;
}

.panel {
  flex: 1;
  transition: flex 0.4s ease;
  overflow-y: auto;
  border: 1px solid #ccc;
}

.panel:hover {
  flex: 2;
}


</style>