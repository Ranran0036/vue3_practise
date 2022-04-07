<template>
	<h1>一个人的信息</h1>
	<h2>姓名：{{name}}</h2>
	<h2>年龄： {{age}}</h2>
	<button @click="changeInfo">Change Info</button>
</template>

<script>
import { ref } from '@vue/reactivity';
export default {
    name: 'App',
	setup () {
		let name = ref('Tom Cruise');
		let age = ref(56);

		function changeInfo (){
			name.value = 'Tom Hanks';
			age.value = 68
		}

		return {
			name,
			age,
			changeInfo
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
