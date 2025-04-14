
<template>
    <div id="search">
        <form @submit.prevent="$emit('filter', filter)">
            <input id="search" type="text" placeholder="Search" v-model="filter.name"/>
            <button type="button" v-on:click="this.showAdvanced">^</button>
            <div v-if="show">
                <label for="min_date">min date:</label>
            <input id="min_date" type="date" v-model="filter.min_date"/>
            <label for="max_date">max date:</label>
            <input id="max_date" type="date" v-model="filter.max_date"/>
            <label id="gender"></label>
            <select id="gender" v-model="filter.gender">
                <option></option>
                <option>male</option>
                <option>remove</option>
            </select>
            <label for="contact">contact:</label>
            <input id="contact" v-model="filter.contact"/>
            <label for="condition">condition:</label>
            <input id="condition" v-model="filter.condition"/>
            </div>
            <input id="submit" type="submit" label="Search"/>

        </form>
    </div>
</template>
<script>
export default {
    data() {
        return {
            filter:{
                name: "",
                min_date: "",
                max_date: "",
                gender: "",
                contact: "",
                condition: "",
            },
            show: false,
        }
    },
    emits:['filter'],
    methods:{
        showAdvanced(){
            console.log("showAdvanced");
            this.show = !this.show;
        }
    }
}
</script>
<style scoped>
</style>