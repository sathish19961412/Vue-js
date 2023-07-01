<template>
    <form @submit.prevent="handleSubmit"  class="from">
        <div class="form-group">
            <label>Employee Name</label>
            <input type="text" class="form-control" v-model="employee.name" name="employeename" 
            :class="{'has-error':submitting&&invalidName}"
            @focus="clearStatus"
            @keypress="clearStatus"
            ref="firstInput"
            > 
        </div>
         <div class="form-group">
            <label>Employee Email</label>
            <input type="email" class="form-control" v-model="employee.email" name="employeemail"
             :class="{'has-error':submitting&&invalidEmail}"
                @focus="clearStatus"
                @keypress="clearStatus"
             > 
        </div>
        <p v-if="submitting && error" class="error-message">Pls Fill Out All The Required Fileds</p>
        <p v-if="success" class="success-message">success full added to the data</p>
        <button class="btn btn-info">Add Employee</button>
    </form>
</template>

<script>
export default{
    name:'employee-form',
    data(){
        return{
            submitting:false,
            success:false,
            error:false,
            employee:{
                name:'',
                email:''
            }
        }
    },
    methods:{
        handleSubmit(){
            this.submitting=true;
            this.clearStatus();

            if(this.invalidName||this.invalidEmail)
            {
                this.error=true;
                return;
            }

            this.$emit('add:employee',this.employee);
            this.$refs.firstInput.focus();

            this.employee={
                name:'',
                email:''
            };

            this.success=true;
            this.error=false;
            this.submitting=false;
        },
        clearStatus(){
            this.success=false;
            this.error=false;
        }
    },
    computed:{
    invalidName(){
      return this.employee.name==='';
    },
    invalidEmail(){
      return this.employee.email=='';
    }
  }
}
</script>

<style scoped>
     .has-error{
        border:1px solid #e20909cc;
     }
     .error-message{
        color:#af2121
     }
     .success-message{
        color:#008000
     }
</style>