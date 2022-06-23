<template>
  <input type="text" v-model="keyword" />
  <!-- <h6>{{ keyword }}</h6> -->
  <h6>{{ result }}</h6>
</template>

<script lang="ts">
import { defineComponent } from "vue";
// 导入ref
import { ref, computed } from "vue";
export default defineComponent({
  name: "App",
  // 组合式API入口

  setup() {
    // 需求 查找关键字
    // 解题思路
    // 1. 保存输入的关键词，keyword
    // 1.5 filter 过滤之后的结果是 list
    // 2 .从names 列表中过滤出包含该字段的列表 （includes）
    const names = ref([
      "林俊杰",
      "孙燕姿",
      "周杰伦",
      "张惠妹",
      "刘若英",
      "林宥嘉",
      "刘德华",
      "张韶涵",
      "周笔畅",
      "孙楠",
    ]);
    // 搜索的值
    //ref 属性.value 获取该值
    const keyword = ref("");
    // computed 应用
    const result = computed(() => {
      return names.value.filter((x) => x.includes(keyword.value));
    });

    // 返回值
    return { keyword, result };
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
