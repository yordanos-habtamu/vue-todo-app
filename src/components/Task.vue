<template>
<div @dblclick="$emit('btn-click',task.id)"  :class="[task.reminder ? 'reminder' : '' ,'task']">
<h3>{{ task.text }}
    <i @click="$emit('deleteTask',task.id)" class="fa-solid fa-xmark"></i>
</h3>
<p>{{ task.day }}</p>
</div>
</template>
<script>
export default {
    name: 'Task',
    props:{
     task:Object
    }
}
</script>
<style scoped>
 .task{
    background:#f4f4f4;
    margin:5px;
    padding:10px 20px;
    cursor:pointer;
 }
 .task.reminder{
    border-left: 5px solid green;
 }
 .task h3{
    display: flex;
    align-items: center;
    justify-content:space-between;
 }
 .fa-solid {
    color:red;
 }
</style>