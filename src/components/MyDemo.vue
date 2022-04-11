<template>
    <h2>当前求和为： {{sum}}</h2>
    <button @click="sum++">点我加1</button>
    <h2>当前的信息为： {{msg}}</h2>
    <button @click="msg += '!'">点我改变</button><hr>
    <h2>姓名：{{person.name}} &nbsp; 年龄：{{person.age}} &nbsp; 薪资：{{person.job.job1.salary}}K</h2>
    <button @click="person.age++">点我增加年龄</button>
    <button @click="person.name += '~'">点我修改姓名</button>
    <button @click="person.job.job1.salary++">点我增加薪资</button>
</template>

<script>
import { ref , reactive} from '@vue/reactivity';
import { watchEffect } from '@vue/runtime-core';
export default {
    //定义组件名
    name : 'MyDemo',

    // 初始化数据
    setup () {
        let sum = ref(1);

        let msg = ref('hello');

        let person = reactive({
            name : 'Tom Cruise',
            age : 56,
            job : {
                job1 : {
                    salary : 10
                }
            }
        });

        watchEffect(() => {
            console.log('sum变化了 新值为：' , sum.value );
        })

        return {
            sum,
            msg,
            person
        }
    }
}
</script>
