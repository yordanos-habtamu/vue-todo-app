<template>
   <form @submit="onSubmit" class="add-form">
     <div class="form-control">
       <label>Task</label>
       <input type="text" v-model="text" name="text" placeholder="add task" />
     </div>
     <div class="form-control">
       <label>Day and time</label>
       <input type="text" v-model="day" name="day" placeholder="add day and time" />
     </div>
     <div class="form-control form-control-check">
       <label>Set Reminder</label>
       <input type="checkbox" v-model="reminder" name="reminder" />
     </div>
     <input type="submit" value="Save task" class="btn btn-block">
   </form>
 </template>
 
 <script>
 export default {
   name: 'AddTask',
   data() {
     return {
       text: '',
       day: '',
       reminder: false
     }
   },
   methods: {
     onSubmit(e) {
       e.preventDefault()
 
       if (!this.text) {
         alert('Please insert the task')
         return
       }
 
       const newTask = {
         id: Math.floor(Math.random() * 100000),
         text: this.text,
         day: this.day,
         reminder: this.reminder
       }
    this.$emit('add-task',newTask)
       this.text = ''
       this.day = ''
       this.reminder = false
     }
   }
 }
 </script>
 
 <style scoped>
 .btn.btn-block {
   display: inline-block;
   padding: 10px 20px;
   background-color: #007bff;
   color: #fff;
   font-size: 16px;
   border: none;
   border-radius: 4px;
   cursor: pointer;
   text-align: center;
   text-decoration: none;
 }
 .form-control-check {
   display: flex;
   align-items: center;
   justify-content: space-between;
 }
 .add-form {
   margin-bottom: 40px;
 }
 .form-control {
   margin: 20px 0;
 }
 .form-control {
   display: block;
 }
 .form-control input {
   width: 100%;
   height: 40px;
   margin: 5px;
   padding: 3px 7px;
   font-size: 17px;
 }
 .form-control-check {
   display: flex;
   align-items: center;
   justify-content: space-between;
 }
 .form-control-check label {
   flex: 1;
 }
 .form-control-check input {
   flex: 2;
   height: 20px;
 }
 </style>
 