<template>
<section>
  <div class="container">
      <div class="row">
          <div class="col-md-12">
            <div class="employee1">
                <h1>Employees Form</h1>
            </div>
            <div class="employee1">
              <employee-form @add:employee="addEmployee"/>
            </div>
          </div>
      </div>
      <div class="row mt-5">
          <div class="col-md-1"></div>
          <div class="col-md-10">
            <div class="employee1">
                <h1>Employees Table</h1>
            </div>
            <div class="employee1">
              <employee-table :employees="employees" @delete:employee="deleteEmployee"/>
            </div>
          </div>
          <div class="col-md-1"></div>
      </div>
  </div>
</section>
</template>

<script>
import EmployeeTable from './components/EmployeeTable.vue';
import EmployeeForm from  './components/EmployeeForm.vue';
import './assets/css/responsive.css';
export default {
  name: 'App',
  components: {
     EmployeeTable,
     EmployeeForm
  },
  data(){
    return{
        employees:[
          {
            id:1,
            name:'Sathish Mathew',
            email:'sathishmathew@gmail.com'
          },
          {
            id:2,
            name:'Guru Prasath',
            email:'sathishmathew@gmail.com'
          },
          {
            id:3,
            name:'Mathew Sathish',
            email:'sathishmathew@gmail.com'
          }
        ]
    }
  },
  methods:{
    addEmployee(employee){
          const lastId =this.employees.length>0?this.employees[this.employees.length-1].id:0;
          const id =lastId+1;
          const newEmployee = {...employee,id}
          this.employees =[...this.employees,newEmployee];
    },
    deleteEmployee(id){
      this.employees =this.employees.filter((employee)=>{
                return employee.id !=id;
      })
    }
  }

}
</script>

<style>
.employee1
{
  display:flex;
  justify-content: center;
}
</style>
