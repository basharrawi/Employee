<template>

  <nav class="navbar navbar-light bg-light">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">
      <h2>Employee ID cards</h2>
    </a>
  </div>
</nav>
    
  
 
 <div class="row">
    <div class='parent' v-for="employee in employees" :key="employee.id" style="width: 21rem;">
      <div class="card" style="width: 20rem;">
        <div class="card-body">
          <h5 class="card-title">Employee number: {{employee.id}} <span class="badge rounded-pill bg-info text-dark">{{employee.firstname}}</span></h5>
          <h4 class="card-subtitle mb-2 text-muted">{{employee.firstname}} {{employee.lastname}} </h4>
          <h6 class="card-subtitle mb-2 text-muted">E-mail: {{employee.email}}</h6>
          <h6 class="card-subtitle mb-2 text-muted">Phone: {{employee.phone}}</h6>
          <button type="button" class="btn btn-primary" data-bs-toggle="modal" :data-bs-target="'#edit' + employee.id" >Edit</button>
          <button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#d" @click="deleteEmployee(employee.id)">Delete</button>
        </div>
      </div>
    </div>
</div>
<edit-employee/>
</template>


<script>
import axios from "axios";

import EditEmployee from '../components/EditEmployee.vue';



export default {
  name: 'employee-table',
  components: {
      EditEmployee
    
  },
 
  data() {
    return {
      employees: {}
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
.parent {
  margin: 1rem;
  padding: 2rem 2rem;
  text-align: left;
  
}
.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  }
button {
  margin-right: 0.5rem;
}

.empty-table {
  color: #d33c40;
  font-weight: bolder;
}
.row {margin: 0 -5px;
}
.row:after {
  content: "";
  display: table;
  clear: both;
}
.card-title {
  text-align: center;
}
</style>



