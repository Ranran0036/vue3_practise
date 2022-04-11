<template>
	<h1>一个人的信息</h1>
	<h2>姓名：{{name}}</h2>
	<h2>年龄： {{age}}</h2>
	<h3>职业：{{job.work}}</h3>
	<h3>薪水：{{job.salary}}</h3>
	<button @click="changeInfo">Change Info</button>
</template>

<script>
	import { reactive, ref } from '@vue/reactivity';
	export default {
		name: 'App',
		setup () {
			let name = ref('Tom Cruise');
			let age = ref(56);
			let job = reactive({
				work : 'actor',
				salary : '30k'
			});

			function changeInfo (){
				job.work = 'artist';
				job.salary = '40k';
			}

			return {
				name,
				age,
				changeInfo,
				job
			}
		}
	}
</script>

<style>
	#app {
		font-family: Avenir, Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
	}
</style>
