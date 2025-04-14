<script setup>
import AddPatient from './components/AddPatient.vue'
import ViewAllPatient from './components/ViewAllPatient.vue'
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
      <ViewAllPatient />
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


</style>