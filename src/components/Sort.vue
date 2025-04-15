<script setup>

    const props = defineProps(['sortBy'])
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
</style>