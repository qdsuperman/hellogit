<template>
  <h2>Child子级组件</h2>
  <h4>msg:{{ msg }}</h4>
  <button @click="update">更新数据</button>
</template>
<script lang="ts">
import { defineComponent, ref,onBeforeMount,onMounted,onBeforeUpdate,onUpdated,onBeforeUnmount,onUnmounted } from "vue";
export default defineComponent({
  name: "Child",
  //vue2.x中的生命周期钩子
  beforeCreate() {
    console.log("vue2.x中的beforeCreate...");
  },
  created() {
    console.log("vue2.x中的Create...");
  },
  beforeMount() {
    console.log("vue2.x中的beforeMount...");
  },
  mounted() {
    console.log("vue2.x中的mounted...");
  },
  beforeUpdate() {
    console.log("vue2.x中的beforeUpdate...");
  },
  updated() {
    console.log("vue2.x中的updated...");
  },
  beforeUnmount() {
    console.log("vue2.x中的beforeUnmount...");
  },
  unmounted() {
    console.log("vue2.x中的unmounted...");
  },

  setup() {
    //响应式的数据
    const msg = ref("abc");
    //按钮点击事件的回调
    const update = () => {
      msg.value += "===";
    }
    onBeforeMount(()=>{
        console.log('vue3.0中的onBeforeMount')
    })
    onMounted(()=>{
        console.log('vue3.0中的onMounted')
    })
    onBeforeUpdate(()=>{
        console.log('vue3.0中的onBeforeUpdate')
    })
    onUpdated(()=>{
        console.log('vue3.0中的onUpdated')
    })
    onBeforeUnmount(()=>{
        console.log('vue3.0中的onBeforeUnmount')
    })
    onUnmounted(()=>{
        console.log('vue3.0中的onUnmounted') 
    })

    
    return {
      msg,
      update,
    };
  },
});
</script>