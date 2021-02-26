<template>
  <h2>setup和ref</h2>
  <h3>{{count}}</h3>
  <button @click="updateCount">更新数据</button>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'App',

setup(){
//变量
const count = ref(0)
console.log(count)
//方法
function updateCount(){
  //count++
  count.value++
}
//返回的是一个对象
  return{
    count,
    //属性
    updateCount
    //方法
  }
}
 
})
</script>

