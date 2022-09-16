<template>
<section>
  <div class="container">
      <div class="row">
          <div class="col-md-1"></div>
          <div class="col-md-10">
            <div class="employee1">
                <h1>Employees</h1>
            </div>
            <div class="employee1">
              <employee-table-vue />
            </div>
          </div>
          <div class="col-md-1"></div>
      </div>
  </div>
</section>
  
</template>

<script>
import EmployeeTableVue from './components/EmployeeTable.vue';
export default {
  name: 'App',
  components: {
     EmployeeTableVue
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
