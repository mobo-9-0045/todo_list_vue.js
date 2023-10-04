<script lang="ts">
 import Header  from "./components/Header.vue";
 import Tasks from "./components/Tasks.vue";
 import AddTask from "./components/AddTask.vue";

 interface Itasks
 {
   id: number;
   desc: string;
   reminder :boolean;
  }
  export default{
  name: 'App',
  components : {
    Header,
    Tasks,
    AddTask,
  },
  data(){
    return {
      tasks :[] as Itasks[],
    }
  },
  created(){
    // const newTask :Itasks = {
    //   id : 1,
    //   desc : "sport at um6p pol sport",
    //   reminder : true,
    // };
    // const task2: Itasks = {
    //   id: 2,
    //   desc: "Study for exam",
    //   reminder: false,
    // };
    // this.tasks.push(newTask, task2);
  },
  methods:
  {
    deleteTask(id:number){
      if (confirm("Are you sure")){
        this.tasks = this.tasks.filter((task) => task.id !== id);
        console.log(`task deleting function ${id}`);
      }
    },
    Addtask (task : Itasks){
      this.tasks = [...this.tasks, task];
    }
  }
}
</script>

<template>
  <Header title="Task tracker"/>
  <div class="h-screen w-screen bg-black text-white">
    <div class="h-full flex flex-col justify-center items-center">
      <AddTask @add-task="Addtask"/>
      <Tasks @delete-task="deleteTask" v-bind:Tasks="tasks" />
    </div>
  </div>
</template>