<template>
	<form class="flex flex-col justify-center items-center" @submit="Submit">
		<div class="text-white flex flex-col">
			<label class="text-center text-3xl">Task</label>
			<input type="text" v-model="desc" name="text" placeholder="Add Task" class="text-black m-2 p-2 rounded-lg"/>
		</div>
		<div class="flex flex-row justify-center items-center">
			<label class="text-xl text-white p-2">Set Reminder</label>
			<input type="checkbox" name="reminder" v-model="reminder"/>
		</div>
		<input type="submit" value="Save Task" class="bg-green-500 w-20 h-10 rounded-md" />
	</form>
</template>

<script lang="ts">
	interface Itasks
 {
   id: number;
   desc: string;
   reminder :boolean;
  }
	export default{
		name : "AddTask",
		data(){
			return {
				desc : '',
				reminder : false
			}
		},
		methods :{
			Submit(e : Event){
				console.log("submit function called");
				e.preventDefault();
				if (!this.desc){
					alert("please insert a new task");
					return;
				}
				const newTask : Itasks = {
					id: Math.floor(Math.random() * 1000),
					desc : this.desc,
					reminder : this.reminder,
				}
				this.$emit("add-task", newTask);
				this.desc = "";
				this.reminder = false;
			}
		}
	}
</script>