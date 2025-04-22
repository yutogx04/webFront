<script setup>

    const props = defineProps({
        sortBy:{
            var: "",
            ascending: true,
        }})
    const emits=defineEmits(['sort'])
</script>

<template>
    <form @submit.prevent="$emit('sort')">
        <select v-model="sortBy.var">
            <option value="">Sort By</option>
            <option value="name">Name</option>
            <option value="date">Date</option>
            <option value="gender">Gender</option>
            <option value="contact">Contact</option>
            <option value="condition">Condition</option>
        </select>
        <select v-model="sortBy.ascending">
            <option value="true">Ascending</option>
            <option value="false">Descending</option>
        </select>
        <input type="submit" value="Sort" />
    </form>
</template>

<style scoped>
select {
  flex: 2 1 300px;
  min-width: 0;
  padding: 0.5rem 0.75rem;
  border: 1px solid var(--border-color);
  border-radius: 6px;
  font-size: 1rem;
  width: 200px;
  background-color: var(--surface);
  color: var(--text-primary);
}
input {
  width: 60px;
  padding: 0.5rem 0.75rem;
  background-color: var(--primary);
  color: #fff;
  font-weight: 600;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.3s ease;
}
</style>