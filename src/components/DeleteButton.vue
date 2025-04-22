<script setup>
import axios from 'axios';
const props = defineProps(['_id'])
const deletePatient=function() {

   if(confirm("Do you really want to delete?")){

    console.log("deleting patient");
    axios.delete('http://localhost:3000/' + props._id)
        .then(function (response) {
            console.log(response);
        })
        .catch(function (error) {
            console.log(error);
        });
   }
   window.location.reload()
}
</script>

<template>
    <button id="delete" @click="deletePatient">X</button>
</template>

<style scoped>
</style>