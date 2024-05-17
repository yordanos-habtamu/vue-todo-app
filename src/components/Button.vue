<template>
    <button @click="onClick" class="button" :style="{background:color}">{{text}}</button>
</template>
<script>
export default {
    name:'Button',
    props:{
        color:String,
        text:String,
      
    },
    methods:{
        onClick(){
           this.$emit('btn-click')
        }
    }
}
</script>
<style scoped>
.button {
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


</style>