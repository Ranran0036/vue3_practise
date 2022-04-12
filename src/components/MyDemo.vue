<template>
    <h2>
        姓名：{{ person.name }} &nbsp; 年龄：{{ person.age }} &nbsp; 薪资：{{
            person.job.job1.salary
        }}K
    </h2>
    <button @click="age++">点我增加年龄</button>
    <button @click="name += '~'">点我修改姓名</button>
    <button @click="salary++">点我增加薪资</button>
</template>

<script>
import { reactive, toRef, toRefs } from "@vue/reactivity";
export default {
    //定义组件名
    name: "MyDemo",

    // 初始化数据
    setup() {
        let person = reactive({
            name: "Tom Cruise",
            age: 56,
            job: {
                job1: {
                    salary: 10,
                },
            },
        });

        //解构赋值
        let { name, age } = toRefs(person);
        //toRefs 只会为源对象中包含的 property 生成 ref。如果要为特定的 property 创建 ref，则应当使用 toRef
        let salary = toRef(person.job.job1, "salary");

        return {
            person,
            name,
            age,
            salary,
        };
    },
};
</script>
