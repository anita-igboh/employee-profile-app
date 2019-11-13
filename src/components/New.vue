<template>
  <tr>
    <td>{{item.id}}</td>
    <td>{{item.employee_name}}</td>
    <td>{{item.employee_salary}}</td>
    <td>{{item.employee_age}}</td>
    <button class="btn" @click="deleteItem">Delete</button>
    <button class="btn_1" @click="editItem">Edit</button>
  </tr>
</template>

<script>
export default {
  name: "New",
  props: {
    item: Object
  },
  methods: {
    deleteItem() {
      this.$http
        .delete(`http://dummy.restapiexample.com/api/v1/delete/${this.item.id}`)
        .then(response => {
          alert(" Deleted Successfully");
          console.log(response);
          this.$emit("reload");
        })
        .catch(error => {
          alert("Error Deleting ");
          console.log(error.response);
        });
    },
    editItem() {
      this.$router.push({ name: "edit", params: { id: this.item.id } });
    }
  }
};
</script>
<style scoped>
.btn {
  margin-right: 5px;
  margin-top: 20px;
}
</style>