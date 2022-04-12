<template>
    <button @click="switchShowDemo">切换隐藏/显示</button>
    <MyDemo v-if="isShowDemo"></MyDemo>
</template>

<script>
import MyDemo from "./components/MyDemo";
import { ref } from "@vue/reactivity";

export default {
    name: "App",
    components: {
        MyDemo,
    },
    setup() {
        let isShowDemo = ref(true);

        function switchShowDemo() {
            isShowDemo.value = !isShowDemo.value;
        }

        return {
            isShowDemo,
            switchShowDemo,
        };
    },
};
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
