<template>
    <h2>当前求和为： {{ sum }}</h2>
    <button @click="sum++">点我加1</button>
    <hr />
    <h2>当前鼠标点击的坐标为：x-{{ point.x }} , y-{{ point.y }}</h2>
</template>

<script>
import { ref } from "@vue/reactivity";
import usePoint from "../hooks/usePoint";
export default {
    //定义组件名
    name: "MyDemo",

    // 初始化数据
    setup() {
        let sum = ref(1);

        let point = usePoint();

        return {
            sum,
            point,
        };
    },
};
</script>
