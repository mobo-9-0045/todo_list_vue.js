<script lang="ts">
  import Task from "./Task.vue";
  interface Itasks
  {
    id: number;
    desc: string;
    reminder :boolean;
  }
  export default{
    name : 'Tasks',
    props :{
      Tasks:Array as () => Itasks[]
    },
    components :{
      Task,
    },
    emits : ["delete-task"],
    methods:{
      onDelete(id: number){
        this.$emit("delete-task", id);
        console.log(`id in tasks ${id}`);
      }
    }
  }
</script>

<template>
	<div v-for="task in Tasks" :key="task.id" class="bg-slate-900 h-auto w-1/3 rounded-lg p-4 m-5">
    <Task @delete-task="onDelete(task.id)" :task="task"/>
  </div>
</template>
