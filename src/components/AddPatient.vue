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
            if(!this.first_name.match(/^[_a-zA-Z0-9]/)){
                alert("First name cannot contain special characters")
                return
            }
            if(!this.last_name.match(/^[_a-zA-Z0-9]/)){
                alert("Last name cannot contain special characters")
                return
            }

            if(new Date(this.date_of_birth)>Date.now()){
                alert("date is not valid")
                return;
            }
            if(!this.contact.match(/^[_a-zA-Z0-9.,@]/)){
                alert("Contact cannot contain special characters")
                return
            }
            if(!this.condition.match(/^[_a-zA-Z0-9,.]/)){
                alert("Condition cannot contain special characters")
                return
            }
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
                window.location.reload();
            })
            .catch(function (error) {
                alert("Error adding patient try again later");
                console.log(error);
            })
        }
    }
}
</script>
<template>
  <div id="AddPatient">
    <h2>Add New Patient</h2>
    <form @submit.prevent="submit">
      <div>
        <label for="firstName">First Name</label>
        <input
          id="firstName"
          v-model="first_name"
          type="text"
          placeholder="First Name"
          required
        />
      </div>

      <div>
        <label for="lastName">Last Name</label>
        <input
          id="lastName"
          v-model="last_name"
          type="text"
          placeholder="Last Name"
          required
        />
      </div>

      <div>
        <label for="dob">Date of Birth</label>
        <input
          id="dob"
          v-model="date_of_birth"
          type="date"
          required
        />
      </div>
      <div>
        <label for="gender">Gender</label>
        <select id="gender" required v-model="gender">
          <option>male</option>
          <option>female</option>
        </select>
      </div>
      <div>
        <label for="contact">Contact</label>
        <input
          id="contact"
          v-model="contact"
          placeholder="example@domain.com"
          required
        />
      </div>

      <div>
        <label for="condition">Condition</label>
        <input
          id="condition"
          v-model="condition"
          type="text"
          placeholder="..."
          required
        />
      </div>

      <input type="submit" label="Submit"/>
    </form>
  </div>
</template>


<style scoped>
/* Form Styles */
h2 {
  font-size: 1.5rem;
  margin-bottom: 1.5rem;
  color: var(--text-primary);
  text-align: center;
}

#AddPatient {
  max-width: 600px;
  width: 90%;
  margin: 2rem auto;
  padding: 2rem;
  background-color: var(--surface);
  border: 1px solid var(--border-color);
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.04);
  position: relative;
  z-index: 1;
}

#AddPatient > div {
  display: flex;
  flex-direction: row;
  align-items: center;
  margin-bottom: 1rem;
  flex-wrap: wrap;
}

label {
  flex: 1 0 150px;
  margin-bottom: 0.5rem;
  font-weight: 500;
  color: var(--text-secondary);
}

input , select {
  flex: 2 1 300px;
  min-width: 0;
  padding: 0.5rem 0.75rem;
  border: 1px solid var(--border-color);
  border-radius: 6px;
  font-size: 1rem;
  width: 100%;
  background-color: var(--surface);
  color: var(--text-primary);
}

input[type="submit"] {
  width: 100%;
  padding: 0.75rem;
  background-color: var(--primary);
  color: #fff;
  font-weight: 600;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

input[type="submit"]:hover {
  background-color: var(--primary-dark);
}

/* Responsive */
@media (max-width: 600px) {
  #AddPatient {
    padding: 1rem;
  }

  #AddPatient > div {
    flex-direction: column;
    align-items: stretch;
  }

  label {
    flex: 1 0 auto;
    margin-bottom: 0.25rem;
  }

  input {
    flex: 1 0 auto;
    font-size: 0.95rem;
  }
}
</style>
