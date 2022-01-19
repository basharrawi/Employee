<template>
    <table class="table">
     <thead>
        <tr>
        <th scope="col">ID</th>
        <th scope="col">First name</th>
        <th scope="col">Last name</th>
        <th scope="col">E-mail</th>
        <th scope="col">Phone</th>
        <th scope="col">Actions</th>
            
        </tr>
     </thead>
     <tbody>
         <tr v-for="employee in employees" :key="employee.id">
             <th scope="row">{{employee.id}}</th>
             
             <td>{{employee.firstname}}</td>
             <td>{{employee.lastname}}</td>
             <td>{{employee.email}}</td>
             <td>{{employee.phone}}</td>
             <td>
                 <button type="button" class="btn btn-primary" data-bs-toggle="modal" :data-bs-target="'#edit' + employee.id">Edit</button>
                 <button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#d" @click="deleteEmployee(employee.id)">Delete</button>
                
            </td>
         </tr>
     </tbody>   
    </table>
    
<EditEmployee/>

    
</template>

<script>
import axios from "axios";
import EditEmployee from './EditEmployee.vue'


export default {
  name: 'employee-table',
  components: {
        EditEmployee
    
  },
 
  data() {
    return {
      employees: []
    }
  },
  created(){
    
    axios
      .get('http://localhost:3000/employees/')
      .then (response => {
         this.employees = response.data
      })
      
      .catch (error => {
        console.log('There was an error:' + error.response)
      })
  },
  methods:{
    deleteEmployee(id){
      let response = confirm(`Are you sure you want to delete employee?`)
      if(response)
    {
      axios.delete('http://localhost:3000/employees/'+id)
      .then (() => {
         this.getEmployee
      })
    }}
  },
  getEmployee(){
    
    axios
      .get('http://localhost:3000/employees/')
      .then (response => {
         this.employees = response.data
      })
      
      .catch (error => {
        console.log('There was an error:' + error.response)
      })

  }
  
}


</script>

<style scoped>
button {
  margin-right: 0.5rem;
}

.empty-table {
  color: #d33c40;
  font-weight: bolder;
}
</style>