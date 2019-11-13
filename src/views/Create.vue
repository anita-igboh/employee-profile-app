<template>
  <div>
    <h2>ADD NEW EMPLOYEE</h2>
    <form @submit.prevent="createItem">
      <label for="name">Employee Name</label>
      <input type="text" placeholder="...name" v-model="anyName.employee_name" />
      <br />
      <br />
      <label for="name">Employee's Salary</label>
      <input type="number" placeholder="...salary" v-model="anyName.employee_salary" />
      <br />
      <br />
      <label for="name">Employee's Age</label>
      <input type="number" placeholder="...age" v-model="anyName.employee_age" />
      <br />
      <br />
      <button class="abt_btn" @click="createItem">Create</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "Create",
  data() {
    return {
      anyName: {
        employee_name: "",
        employee_salary: "",
        employee_age: ""
      }
    };
  },

  methods: {
    createItem() {
      this.$http
        .post("http://dummy.restapiexample.com/api/v1/create", this.anyName)
        .then(response => {
          this.anyName = {
            employee_name: "",
            employee_salary: "",
            employee_age: ""
          };
          alert(`Successfully added item ${response.data.id}`);
        })
        .catch(error => {
          alert(error.response);
        });
    }
  }
};
</script>

<style scoped>
h2 {
  color:rgb(250, 67, 67);
}
label {
  display: block;
}
form {
  display: block;
  margin: 2rem auto;
}
input {
  width: 30%;
  padding: 12px 20px;
  margin: 8px 0;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

label {
  font-size: 15px;
  font-weight: bold;
}
.abt_btn {
  padding: 1rem 1rem;
  background: rgb(250, 67, 67);
  color: #fff;
  /* margin-right: 60px; */
  border-radius: 4px;
}
</style>