<script setup>
import DeleteButton from './DeleteButton.vue';
const props= defineProps({
    _id: Number,
    first_name: String,
    last_name: String,
    date_of_birth: String,
    gender: String,
    contact: String,
    condition: String,
})

</script>
<template>
    <div id="card">
        <h1 id="name"> {{ first_name }} {{ last_name }}</h1>
        <div id="info">
            <div>
                date_of_birth: {{ date_of_birth }} <br>
                contact: {{ contact }}
            </div>
            <div>
                gender: {{ gender }} <br>
                condition: {{ condition }}
           </div>
        </div>
        <!-- <DeleteButton :_id="_id">X</DeleteButton> -->
    </div>
</template>
<style scoped>
#card {
  max-width: 600px;
  margin: 2rem auto;
  padding: 2rem;
  background-color: var(--surface);
  border: 1px solid var(--border-color);
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.04);
  position: relative;
  z-index: 1;
}


#card > div{
  display: flex;
}


#card > div > div{
  margin: 5px;
}

label {
  flex: 1 0 150px;
  margin-bottom: 0.5rem;
  font-weight: 500;
  color: var(--text-secondary);
}

@media (max-width: 600px) {
  label {
    flex: 1 0 auto;
    margin-bottom: 0.25rem;
  }
  #card {
    padding: 1rem;
  }
}
</style>