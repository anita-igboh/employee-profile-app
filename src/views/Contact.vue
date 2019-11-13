<template>
<div>
    <h1>LIST OF EMPLOYEES</h1>
         <table>
            <tr >
                <th>id</th>
                <th>Employee Name</th>
                <th>Employee's Salary</th> 
                <th>Employee's Age</th>
                <th></th>
            </tr>
            <New v-for="list in newsUpdate" :key="list.id" 
            :item='list'
            @reload= 'deleteValue()'></New>
          </table>
</div>
</template>

<script>
import New from '@/components/New.vue'
export default {
    name: 'contact',
    components: {
        New
    },
data() {
return {
    newsUpdate: []
}
},
methods: {
    deleteValue() {
        this.$http.get('http://dummy.restapiexample.com/api/v1/employees')
    .then(response=> {
        this.newsUpdate = response.data
    })
    .catch(error => {
        console.log(error.response)
    })
    }
},
mounted() {
    this.deleteValue() 
},

};
</script>

<style scoped>

h1 {
   color: rgb(250, 67, 67);
}

table {
  margin-top: 50px;
  border: 1px solid black;
  width: 100vw;
  border-collapse: collapse;
}
td, th {
  border: 1px solid #3333;
  padding: 1rem;
}
tr:nth-child(even) {
background: rgb(248, 67, 67);
}

tr {
    font-size: 18px;
    height: 60px;
}

th {
    font-weight: bold;
    font-size: 1.5em; 
}
</style>