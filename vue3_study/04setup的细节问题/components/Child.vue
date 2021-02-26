<template>
    <h2>Child子级组件</h2>
    <h3>msg:    {{msg}}</h3>
</template>
<script lang="ts">
import { defineComponent } from 'vue'
export default defineComponent({
    name:'Child',
    props:['msg'],
    //setup细节问题：
    //setup是在beforeCreate生命周期回调之前就执行了，而且就执行一次
    //数据初始化的生命周期回调
    beforeCreate(){
        console.log('beforeCreat执行了')
    },

    setup(){
        console.log('setup执行了')
        return{
            //setup中一般都是返回一个对象，对象中的属性和方法都可以在html中直接使用
        }
    }
})
</script>