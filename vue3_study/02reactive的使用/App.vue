<template>
  <h2>reactive的使用</h2>
  <h3>名字{{user.name}}</h3>
  <h3>年龄{{user.age}}</h3>
  <h3>女友{{user.wife}}</h3>
  <hr>
  <button @click="updateUser">更新数据</button>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';

export default defineComponent({
  name: 'App',

//显示用户的相关信息，点击按钮，可以更新用户的相关信息数据
/*
作用: 定义多个数据的响应式
const proxy = reactive(obj): 接收一个普通对象然后返回该普通对象的响应式代理器对象
响应式转换是“深层的”：会影响对象内部所有嵌套的属性
内部基于 ES6 的 Proxy 实现，通过代理对象操作源对象内部数据都是响应式的
*/
setup(){
  //把复杂数据变成响应式数据
  const obj = {
    name:'小明',
    age:20,
    wife:{
      name:'小甜甜',
      age:18,
      cars:['奔驰','宝马','奥迪']
    },
    
  }
  const user = reactive(obj)
  console.log(user);
  

  //function updateUser(){}
  const updateUser = ()=>{
    user.name +='=='
    user.age +=2
    user.wife.name +='++'
    user.wife.cars[0] = '玛莎拉蒂'
    // user.wife.cars[3] = '奥拓'
  }

  return{
    user,
    updateUser
  }
}
 
})
</script>

