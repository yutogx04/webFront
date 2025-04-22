<script setup>
import Search from './Search.vue'
import Patient from './Patient.vue'
import axios from 'axios';
import Sort from './Sort.vue'
import { ref } from 'vue'

const patients= ref([])
const filteredPatients= ref([])
const sortBy = ref({
    var: "",
    ascending: true,
})

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
  sort()
}

const compare = (a,b,c)=>{
  if (b < c) {
    return a === 'true' ? -1 : 1;
  }
  if (b > c) {
    return a === 'true' ? 1 : -1;
  }
  return 0;
};


const sorter =function(patientA,patientB){
  switch (sortBy.value.var){
    case "name":
      return compare(sortBy.value.ascending,
        ( patientA.first_name + patientA.last_name ).toLowerCase(),
        ( patientB.first_name + patientB.last_name ).toLowerCase());
    case "date":
      return compare (sortBy.value.ascending,
        new Date(patientA.date_of_birth) ,
        new Date(patientB.date_of_birth) );
    case "gender":
      return compare (sortBy.value.ascending,
        patientA.gender ,
        patientB.gender );
    case "contact":
      return compare (sortBy.value.ascending,
        patientA.contact.toLowerCase() ,
        patientB.contact.toLowerCase() );
    case "condition":
      return compare (sortBy.value.ascending,
        patientA.condition.toLowerCase() ,
        patientB.condition.toLowerCase());
    default :
      return compare (sortBy.value.ascending,
        patientA._id,
        patientB._id);
  }
}

const sort = ()=>{
  filteredPatients.value.sort((a,b)=>{
     return sorter(a,b)
  })
}


</script>
<template>
    <h2>View All patients</h2>
      <!-- <Search @filter="filter"/> -->
      <Sort @sort="sort" :sortBy="sortBy" />
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
