<template>
  <h4>{{ result }}</h4>

  <button @click="onClickHandler">click result</button>
</template>

<script lang="ts">
import { defineComponent } from "vue";
// 导入ref
import { ref, computed } from "vue";
export default defineComponent({
  name: "App",
  // 组合式API入口

  setup() {
    const num = ref(10);
    // computed只有 发生变化才会执行
    // 否则使用缓存
    const result = computed(() => {
      return num.value * 3;
    });

    const onClickHandler = () => {
      num.value = 15;
    };

    // 返回值
    return { result, onClickHandler };
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
