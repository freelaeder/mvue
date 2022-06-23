<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js + TypeScript App" /> -->
  <h1>{{ name }}{{ age }}</h1>
  <h2>{{ uage }} 00{{ uname }}</h2>
  <button @click="onClickHandler"></button>
  <hr />
  <h3>{{ person.page }} {{ person.pname }}</h3>
  <button @click="ponClickHandler">click person</button>
</template>

<script lang="ts">
import { defineComponent } from "vue";
// import HelloWorld from "./components/HelloWorld.vue";
// 导入ref
import { ref } from "vue";
export default defineComponent({
  name: "App",
  // 组合式·api入口
  // setup 函数执行优先于任何生命周期函数
  // 在setup 定义的普通变量不是响应式数据
  // setup this 指向 undefined
  setup() {
    let name = "freelaeder";
    let age = 20;

    // 响应式数据
    // 使用ref 创建基本数据类型响应数据
    const uname = ref("free");
    const uage = ref(20);

    // 定义方法
    const onClickHandler = () => {
      uage.value = 30;
      uname.value = "new freelaeder";
    };

    // 定义对象
    const person = ref({ pname: "张三", page: 22 });
    const ponClickHandler = () => {
      person.value.pname = "李四";
      person.value.page = 33;
    };

    // 使用reactive
    // 基本数据类型创建不了

    //setup 函数的返回值必须是对象
    // 对象的属性全都会被添加到组件实列中
    //这就意味着选项式API 和模板都可以访问到他
    return { name, age, uname, uage, onClickHandler, person, ponClickHandler };
  },
  components: {
    // HelloWorld,
  },
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
