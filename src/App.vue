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
  <div class="flex-container">
    <div class="panel form-panel">
      <AddPatient />
    </div>
    <div class="panel list-panel">
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
    </div>
  </div>
</template>
<style scoped>
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

ul {
  list-style-type: none;
  padding: 0;
}

#patients {
  width:370px;
  margin: auto;
}
</style>