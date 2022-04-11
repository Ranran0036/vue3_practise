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
import { ref , reactive} from '@vue/reactivity'
import { watch } from '@vue/runtime-core';
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

        //情况一：监视ref所定义的一个响应式数据
        watch( sum, (newValue, oldValue) => {
            console.log('sum变化了 新值为：' + newValue + '，旧值为：' + oldValue);
        })

        //情况二：监视ref所定义的多个响应式数据
        /* watch(
            [sum, msg],
            (newValue, oldValue) => {
                console.log(`sum或msg变化了` , newValue , oldValue);
            },
            //第三个参数：指定是否在第一次触发时触发回调函数
            {
                immediate : true
            }
        ) */
        /* 情况三：监视reractive对象的全部属性
                注意 ： 1 ， 此处无法正确获取oldValue
                       2 ， 强制开启了deep（deep设置false无效）
        */
        /*watch (
            person,
            (newValue, oldValue) => {
                console.log(`person变化了` , newValue , oldValue);
            },
            //第三个参数：指定是否在第一次触发时触发回调函数
            {
                immediate : true
            }
        ) */

        //情况四：监视reactive对象的某个属性
        /* watch(
            () => person.age,
            (newValue, oldValue) => {
                console.log(`person.age变化了` , newValue , oldValue);
            }
        ) */

        //情况五：监视reactive对象的某些属性
        /* watch(
            () => [person.age, person.name],
            (newValue, oldValue) => {
                console.log(`person.age或person.name变化了` , newValue , oldValue);
            }
        ) */

        //特殊情况
        /* watch(
            () => person.job,
            (newValue, oldValue) => {
                console.log(`person.job变化了` , newValue , oldValue);
            },
            //第三个参数：深层监听
            {
                deep : true
            }
        ) */

        return {
            sum,
            msg,
            person
        }
    }
}
</script>
