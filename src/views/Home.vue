<template>
<nav class="navbar navbar-light bg-light">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">
      <h2>Employee List</h2>
    </a>
    <addEmployee/>
  </div>
</nav>
  
  <div class="home">
    
  </div>
  
  <employeeTable/>
  
</template>

<script>
import EmployeeTable from "@/components/EmployeeTable";
import AddEmployee from "@/components/AddEmployee";
// @ is an alias to /src


export default {
  name: 'Home',
  components: {
    AddEmployee,
    EmployeeTable
  }
}
</script>

<style scoped>

.navbar-brand
{
  text-align: center;
}
</style>
