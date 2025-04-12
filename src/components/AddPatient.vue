<script>
import axios from 'axios';
export default{
    data() {
        return {
            first_name: "",
            last_name: "",
            date_of_birth: "",
            gender: "",
            contact: "",
            condition: "",
        }
    },
    methods:{
        submit(){
            axios.post('http://localhost:3000/', {
                    first_name: this.first_name,
                    last_name: this.last_name,
                    date_of_birth: this.date_of_birth,
                    gender: this.gender,
                    contact: this.contact,
                    condition: this.condition,
            })
            .then(function (response) {
                console.log(response);
            })
            .catch(function (error) {
                console.log(error);
            });
        }
    }
}
</script>
<template>
    <div id="add_patient">
        <form @submit="submit">
            <h1>Add Patient</h1>
            <div id="form">
                <div id="labels">
                    <label for="first_name">first_name:</label> <br>
                    <label for="last_name">last_name:</label> <br>
                    <label for="date_of_birth">date_of_birth:</label> <br>
                    <label for="gender">gender:</label> <br>
                    <label for="contact">contact:</label> <br>
                    <label for="condition">condition:</label> <br>
                </div>
                <div id="inputs">
                    <input id="first_name" required v-model="first_name"/> <br>
                    <input id="last_name" required v-model="last_name"/> <br>
                    <input id="date_of_birth" required v-model="date_of_birth" type="date"/> <br>
                    <select id="gender" required v-model="gender">
                        <option>male</option>
                        <option>female</option>
                    </select> <br>
                    <input id="contact" required v-model="contact"/> <br>
                    <input id="condition" required v-model="condition"/> <br>
                </div>
            </div>
            <div id="button">
                <input type="submit" label="Add Patient"/>
            </div>
        </form>
    </div>
</template>
<style scoped>

    #form{
        display: flex;
    }
    form{
        background-color: var(--bg--off-white);
        font-weight:400;
        color: var(--text--black);
        border: 1px solid var(--border);
        border-radius: 8px;
        padding: 0.5rem 0.5rem 0.5rem 1.5rem ;
        div {margin:5px};
        #button {text-align: center;}
    }
    h1{
        margin-left: -0.5rem;
        font-size: 2rem;
        font-weight: bold;
    }
    input[type="submit"]{
        background-color: var(--accent--blue);
        color: var(--text--white);
        border: 1px solid var(--border);
        border-radius: 5px;

        height: 30px;
        width: 70px;
    }
</style>