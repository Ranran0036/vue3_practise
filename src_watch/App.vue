<template>
	<MyDemo></MyDemo>
</template>

<script>
	import MyDemo from './components/MyDemo'
	export default {
		name: 'App',
		components: {
			MyDemo
		},
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
