<script lang="ts">
	export default {
		name: "Header",
		props : {
			title : String,
		},
		methods: {
			clicked(){
				console.log("button clicked");
			}
		}
	}
</script>

<template>
	<header class="bg-black w-full flex flex-row justify-around p-5">
		<h1 class="text-white text-3xl">{{ title }}</h1>
		<button class="bg-green-400 rounded-lg w-20 h-10 text-white" @click="clicked()">click me</button>
	</header>
</template>