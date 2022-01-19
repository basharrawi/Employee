<template>
  <div v-for="employee in employees" :key="employee.id"> 
<!-- Modal -->
<div class="modal fade" :id="'edit' + employee.id" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">Edit contant</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        
        <form @submit.prevent="editcontent(employee.id)" method="update" enctype="multipart/form-date">
        
          <div class="mb-3">
            <label for="First name" class="form-label">First name</label>
            <input type="text" v-model="updating.firstname" class="form-control" id="First name" aria-describedby="emailHelp">
          </div>

          <div class="mb-3">
            <label for="Last name" class="form-label">Last name</label>
            <input type="text"  v-model="updating.lastname" class="form-control" id="Last name" aria-describedby="emailHelp">
          </div>

          <div class="mb-3">
            <label for="email" class="form-label">Email address</label>
            <input type="text" v-model="updating.email" class="form-control" id="email" aria-describedby="emailHelp">
          </div>

          <div class="mb-3">
            <label for="Phone number" class="form-label">Phone number</label>
            <input type="text" v-model="updating.phone" class="form-control" id="Phone number" aria-describedby="emailHelp">
          </div> 
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
            <button type="submit" class="btn btn-success" data-bs-dismiss="modal">Save changes</button>
          </div>
       
        </form>

      </div>
    </div>
  </div>
</div>
</div>
</template>

<script>
import axios from 'axios'

export default {
  
  data() {
    return {
      employees: {
          firstname: '',
          lastname: ''
          },
        employee: {
          firstname: '',
          lastname: ''
        },
        
        updating: {}
       
  }
  
},
mounted (){
    
    axios
      .get('http://localhost:3000/employees/')
      .then (response => {
         this.employees = response.data
      })
      
      .catch (error => {
        console.log('There was an error:' + error.response)
      })
  },
methods: {
   async editcontent (id) {
   const res = axios.patch(`http://localhost:3000/employees/`+id, this.updating )
      this.employees = [res.data];
      }
      
    
   }
  }
  


</script>