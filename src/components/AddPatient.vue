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
    <div id="addContainer">
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
            <input id="submit" type="submit" label="Add Patient"/>
        </form>
    </div>
</template>
<style scoped>

#form{
    display: flex;
    flex-direction: row;
}
form{
    color: var(--text--black);
    padding: 0.5rem 0.5rem 0.5rem 1.5rem ;
    background-color: var(--bg--off-white);
    font-weight: 400;
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 2rem;
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.05);
    transition: all 0.3s ease-in-out;
    width: 430px;
    margin: 2rem auto;
}

form:hover {
    box-shadow: 0 12px 25px rgba(0, 0, 0, 0.1);
    transform: translateY(-2px);
}

form div {
    margin: 1rem 0;
    width:250px;
}


form label {
    font-weight: 500;
    width:100px;
    display: block;
    padding-bottom: 7px;
    padding-top: 7px;
    height: 16px;
}

form input,
form select,
form textarea {
    width:241;
    margin-bottom: 5px;
    padding: 7px 1rem;
    border: 1px solid var(--border);
    border-radius: 6px;
    font-size: 1rem;
    background-color: #fff;
    transition: border 0.2s ease, box-shadow 0.2s ease;
    height: 30px;
    width: 241px;
}

form input:focus,
form select:focus,
form textarea:focus {
    border-color: var(--primary);
    box-shadow: 0 0 0 3px rgba(0, 123, 255, 0.2);
    outline: none;
}


#submit{
    margin: 0 147px;
    width: 70px;
    background-color: var(--bg--off-white);
    color: #fff;
    padding: 0;;
    border: none;
    border-radius: 6px;
    font-size: 1rem;
    font-weight: 500;
    cursor: pointer;
    transition: background-color 0.3s ease, transform 0.2s ease;
}

i#submit:hover {
    background-color: var(--primary-dark);
    transform: scale(1.03);
}
    h1{
        margin-left: -0.5rem;
        font-size: 2rem;
        font-weight: bold;
    }
    /* input[type="submit"]{
        background-color: var(--accent--blue);
        color: var(--text--white);
        border: 1px solid var(--border);
        border-radius: 5px;

        height: 30px;
        width: 70px;
    } */
    #addContainer{
        margin-top: 20%;
        width: 370px;
        margin: auto;
    }
</style>