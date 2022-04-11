<template>
    <h1>一个人的信息</h1>
    姓：<input type="text" v-model="person.firstName" /> <br>
    名：<input type="text" v-model="person.lastName" /> <br>
    <h3>全名：{{person.fullName}}</h3> <br>
    全名：<input type="text" v-model="person.fullName" /> <br>
</template>

<script>
import { reactive } from '@vue/reactivity'
import { computed } from '@vue/runtime-core'
export default {
    //定义组件名
    name : 'MyDemo',

    // 初始化数据
    setup () {
        let person = reactive({
            firstName : 'Tom',
            lastName : 'Cruise'
        })

        //计算属性简写
        /* person.fullName = computed(() => {
            return person.firstName + ' ' + person.lastName
        }) */

        //计算属性完整写法
        person[fullName] = computed({
            get () {
                return person.firstName + ' ' + person.lastName
            },
            set (newValue) {
                let names = newValue.split(' ')
                person.firstName = names[0]
                person.lastName = names[1]
            }
        })

        return {
            person
        }
    }
}
</script>
