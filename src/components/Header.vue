<template>
    <header>
        <h1>{{ title }}</h1>
        <Button 
        @btn-click="$emit('btn-click')" :color="showAddTask ? 'red' : 'green'" :text=" showAddTask ? 'Close' : 'Add Task'"/>
    </header>
</template>
<script>
import Button from './Button.vue'

export default {
    name: 'Header',
    props:{
        title:String,
        showAddTask:Boolean
    },
    components:{
         Button,
    },
    methods:{
       
    }
}
</script>
<style scoped>
header{
    display:flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom:20px;
  }
</style>