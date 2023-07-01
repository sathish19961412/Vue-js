<template>
 <table class="table">
        <thead class="bg-info text-center">
            <tr class="text-white">
                <td>Employee Name</td>
                <td>Employee Email</td>
                <td>Action</td>
            </tr>
        </thead>
        <tbody  class="bg-secondary text-white text-center">
            <tr v-for="employee in employees" :key="employee.id">
                <td>{{employee.name}}</td>
                <td>{{employee.email}}</td>
                <td colspan="2">
                    <button class="btn btn-sm btn-success text-white">Edit</button> 
                    <button @click="$emit('delete:employee',employee.id)" class="btn btn-sm btn-danger text-white">Delete</button>
                </td>
            </tr>
            
        </tbody>
</table>
</template>
<script>

export default {
    name :'employee-table',
    props:{
        employees:Array
    }
}
</script>
<style scoped>
  .btn-sm{
    margin:0px 4px;
  }
</style>