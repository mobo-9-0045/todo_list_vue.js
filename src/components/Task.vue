<template>
  <div v-if="task" class="flex flex-row justify-between items-center">
    <h3 class="text-3xl">-{{ task.desc }}</h3>
    <button @click="onDelete(task.id)" class="text-2xl text-white bg-red-500 text-bold w-20" >X</button>
  </div>
</template>

<script lang="ts">
  export default{
    name : 'Task',
    props : {
      task : Object 
    },
    methods :
    {
      onDelete(id : number){
        this.$emit("delete-task", id);
      }
    }
  }
</script>