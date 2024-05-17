<template>
    <div class="container">
 <Header @btn-click="toggleAddTask"   :showAddTask=showAddTask title="Task tracker"/>
 <div v-if="showAddTask">
   <AddTask @add-task="addTask"/> 
 </div>
 <Tasks @toggle-task="toggleTask" @delete-task="deleteTask" :tasks="tasks"/>
 </div>
</template>
<script>
import Header from './components/Header.vue'
import Tasks from  './components/Tasks.vue'
import AddTask from './components/AddTask.vue'
export default {
    name:'App',
    components:{
        Header,
        Tasks,
        AddTask,
    },
    data(){
        return{
        tasks:[],
        showAddTask:false
        }
    },
     methods: {
        toggleAddTask(){
        this.showAddTask= !this.showAddTask
        },
        addTask(task){
   this.tasks =[...this.tasks,task]
    },
    
    deleteTask(id){
        if(confirm("are you sure?")){
      this.tasks = this.tasks.filter((task) => task.id !== id)
    }},

    toggleTask(id){
       this.tasks=this.tasks.map((task)=>task.id === id ? {...task,reminder:!task.reminder}:task)
    },
    async fetchTask(){
        const res= await fetch('http://localhost:5000/task')
        const data= await res.json()
        return data
    }

    
   },
   async created(){
    this.tasks = await this.fetchTasks()
},
  

}
</script>
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
*{
    box-sizing:border-box;
    margin:0;
    padding:0;
}
body{
    font-family:'poppins',sans-serif;
}
.container{
    max-width:500px;
    margin:30px auto;
    overflow:auto;
    min-height:300px;
    border:1px solid steelblue;
    padding:30px;
    border-radius: 5px;
}
</style>




