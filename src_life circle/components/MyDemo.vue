<template>
    <h2>当前求和为： {{ sum }}</h2>
    <button @click="sum++">点我加1</button>
</template>

<script>
import { ref } from "@vue/reactivity";
import {
    onBeforeMount,
    onBeforeUnmount,
    onBeforeUpdate,
    onMounted,
    onUpdated,
    onUnmounted,
} from "@vue/runtime-core";
export default {
    //定义组件名
    name: "MyDemo",

    // 初始化数据
    setup() {
        let sum = ref(1);

        //通过组合式API使用生命周期钩子
        onBeforeMount(() => {
            console.log("组件初始化完成，开始执行onBeforeMount");
        });

        onMounted(() => {
            console.log("组件完成挂载，开始执行onMounted");
        });

        onBeforeUpdate(() => {
            console.log("组件即将更新，开始执行onBeforeUpdate");
        });

        onUpdated(() => {
            console.log("组件更新完成，开始执行onUpdated");
        });

        onBeforeUnmount(() => {
            console.log("组件即将卸载，开始执行onBeforeUnmount");
        });

        onUnmounted(() => {
            console.log("组件完成卸载，开始执行onUnmounted");
        });

        return {
            sum,
        };
    },

    // 组件生命周期
    /* beforeCreate() {
        console.log("MyDemo beforeCreate");
    },
    created() {
        console.log("MyDemo created");
    },
    beforeMount() {
        console.log("MyDemo beforeMount");
    },
    mounted() {
        console.log("MyDemo mounted");
    },
    beforeUpdate() {
        console.log("MyDemo beforeUpdate");
    },
    updated() {
        console.log("MyDemo updated");
    },
    beforeUnmount() {
        console.log("MyDemo beforeUnmount");
    },
    unmounted() {
        console.log("MyDemo unmounted");
    }, */
};
</script>
