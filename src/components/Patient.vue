<script setup>
defineProps({
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
    </div>
</template>
<style scoped>
#info {
    display: flex;
    div {
        margin: 5px;
    }
}
#card {
    font-weight:400;
    background-color: var(--bg--off-white);
    color: var(--text--black);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 0.5rem 0.5rem 0.5rem 1.5rem ;
}
h1 {
    margin-left: -0.5rem;
    font-size: 2rem;
    font-weight: bold;
    overflow: auto;
}
</style>