<template>
  <h2>计算属性和监视</h2>
  <fieldset>
    <legend>姓名操作</legend>
    姓氏:<input type="text" placeholder="请输入姓氏" v-model="user.firstName"/><br/>
    名字:<input type="text" placeholder="请输入名字" v-model="user.lastName"/><br/>
  </fieldset>
  <fieldset>
    <legend>计算属性和监视的演示</legend>
    姓名:<input type="text" placeholder="显示姓名" v-model="fullName1"/><br/>
    姓名:<input type="text" placeholder="显示姓名" v-model="fullName2"/><br/>
    姓名:<input type="text" placeholder="显示姓名" v-model="fullName3"/><br/>
  </fieldset>
</template>
<script lang="ts">
import { computed, defineComponent, reactive,ref,watch,watchEffect } from 'vue'
export default defineComponent({
  name:'App',
  setup(){
    //定义一个响应式对象
    const user = reactive({
      //姓氏
      firstName:'东方',
      //名字s
      lastName:'不败'
    })
    //通过计算属性的方式，实现第一个姓名的显示
    //vue中的计算属性
    //计算属性的函数中如果只传入一个回调函数，表示的是get
    //第一个姓名：
    //返回的是一个ref类型的对象
    const fullName1 = computed(()=>{
      return user.firstName +'_'+ user.lastName
    })
    //第二个姓名:
    const fullName2 = computed({
      get(){
          return user.firstName +'_'+ user.lastName
      },
      set(val: string){
        const names =val.split('_')
        user.firstName = names[0]
        user.lastName = names[1]
      }
    })

    //第三个姓名：
    const fullName3 = ref('')
    //监视----监视指定的数据
    watch(user,({firstName,lastName})=>{
      fullName3.value = firstName + "_" + lastName
    },{immediate:true,deep:true})
    //immdiate 默认会监视一次watch，deep 深度监视

    //监视，不需要配置immediate，本身默认就会进行监视，（默认执行一次）
    // watchEffect(()=>{
    //   fullName3.value = user.firstName +'_'+ user.lastName
    // })

    //监视fullname3的数据，改变firstname和lastname
    watchEffect(()=>{
      const names = fullName3.value.split('_')
      user.firstName = names[0]
      user.lastName = names[1]
    })

    return{
      user,
      fullName1,
      fullName2,
      fullName3
    }
  }
  
})
</script>