<template>
  <input type="text" v-model="text" />
  <h1>text{{ text }}</h1>
  <h1>person {{ person.name }}</h1>
  <button @click="onClickHandler">click</button>
  <hr />
  <!-- 监听多个值 -->
  <input type="text" v-model="firstName" />
  <input type="text" v-model="lastName" />
</template>

<script lang="ts">
import { defineComponent, watchEffect } from "vue";
// 导入ref
import { ref, watch } from "vue";
export default defineComponent({
  name: "App",
  // 组合式API入口

  setup() {
    // 定义参数
    const text = ref("");

    const person = ref({ name: "freelaeder" });
    const firstName = ref("");
    const lastName = ref("");
    // 定义方法
    const onClickHandler = () => {
      text.value = "haha";
      person.value.name = "new freelader";
    };

    // 要监听的状态

    // 当状态发生变化 执行的回调函数

    // 导入 watch
    // text 要监听的值 current 当前值， previous 之前的值

    // 监听所有值
    // watch(text, (current, previous) => {
    //   console.log(current, "current");
    //   console.log(previous, "previous");
    // });

    // 监听某一个属性具体的值  const person = ref({ name: "freelaeder" });

    // watch(
    //   () => person.value.name,
    //   (current, previous) => {
    //     console.log(current, "current当前的值");
    //     console.log(previous, "previous");
    //   }
    // );

    // 监听多个属性   const firstName = ref('')      const lastName = ref('')
    // 初次加载立即执行 immediate
    // 参数一 监听的多个属性， 属性二 监听的值， 属性三 配置
    watch(
      [firstName, lastName],
      (current) => {
        console.log(current, "watch监听多个属性");
      },
      {
        immediate: true,
      }
    );
    // watchEffected
    watchEffect(() => {
      console.log(firstName.value, "watchEffect监听多个属性");
      console.log(lastName.value, "watchEffect监听多个属性");
    });

    // 返回值
    return { text, person, firstName, lastName, onClickHandler };
  },
  components: {},
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
