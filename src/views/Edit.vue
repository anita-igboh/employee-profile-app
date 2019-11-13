<template>
  <div>
      <h1>EDIT HERE...</h1>
    <label for="name">Name </label>
    <input type="text" v-model="x.employee_name" />
    <br />
    <label for="name">Salary </label>
    <input type="number" v-model="x.employee_salary" />
    <br />
    <label for="name">Age </label>
    <input type="number" v-model="x.employee_age" />
    <br />
    <button class="edit_btn" @click="editNow">Edit</button>
  </div>
</template>

<script>
export default {
  name: "Edit",

  data() {
    return {
      x: {
        employee_name: "",
        employee_salary: "",
        employee_age: ""
      }
    };
  },
  mounted() {
    this.$http
      .get(
        `http://dummy.restapiexample.com/api/v1/employee/${this.$route.params.id}`
      )
      .then(response => {
        this.x = response.data;
      });
  },
  methods: {
    editNow() {
      this.$http
        .put(
          `http://dummy.restapiexample.com/api/v1/employee/${this.$route.params.id}`
        )
        .then(response => {
          console.log(response);
        });
    }
  }
};
</script>

<style scoped>
h1 {
    color: rgb(250, 67, 67);
}
label {
    display: block;
    font-size: 15px;
    font-weight: bold;
}
input {
  width: 30%;
  padding: 12px 20px;
  margin: 8px 0;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

.edit_btn {
  padding: 1rem 1rem;
  background: rgb(250, 67, 67);
  color: #fff;
  margin-left: 50px;
  border-radius: 4px;
  margin-right: 3.5em;
}
</style>