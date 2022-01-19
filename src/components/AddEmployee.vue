<template>

  <div class="hello">
    
    

    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
    
    
      <!-- Button trigger modal -->
<button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#add">
  + Add Employee
</button>

<!-- Modal -->
<div class="modal fade" id="add" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">New employee</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        
        <form @submit.prevent="addnew()" method="post" enctype="multipart/form-date">
          <div class="mb-3">
            <label for="First name" class="form-label">First name:</label>
            <input type="text" v-model="newemployee.firstname" class="form-control" id="First name" aria-describedby="emailHelp">
          </div>

          <div class="mb-3">
            <label for="Last name" class="form-label">Last name:</label>
            <input type="text" v-model="newemployee.lastname" class="form-control" id="Last name" aria-describedby="emailHelp">
          </div>

          <div class="mb-3">
            <label for="email" class="form-label">Email address:</label>
            <input type="text" v-model="newemployee.email" class="form-control" id="email" aria-describedby="emailHelp">
          </div>

          <div class="mb-3">
            <label for="Phone number" class="form-label">Phone number:</label>
            <input type="text" v-model="newemployee.phone" class="form-control" id="Phone number" aria-describedby="emailHelp">
          </div> 
          <button type="submit" class="btn btn-primary" data-bs-dismiss="modal">Submit</button>
        </form>

      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
      </div>
    </div>
  </div>
</div>
</div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'employee-form',
  
  data() {
    return {
      employees: [],

      newemployee:{}
  }
},
methods: {
  async addnew () {
   const res = axios.post('http://localhost:3000/employees/',  this.newemployee);
    this.employees = [res.data];
    
  }
}
}


</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
