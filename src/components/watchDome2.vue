<template>
  <!-- <h1>sss</h1> -->
  <h6>{{ person.age }} {{ person.name }}</h6>
  <button @click="onClickHandler">change age name</button>
  <hr />
  <h6>{{ result }}</h6>
  <input type="text" v-model="search" />
  <h6>{{ filterNames }}</h6>
  <hr />
  <input type="text" v-model="text" name="" id="" />
  <hr />
  <h6>{{ personDome1.name }}</h6>
  <h6>{{ personDome1.age.now }}</h6>
  <button @click="changeDome1">change dome1.name</button>
</template>

<script lang="ts">
import { defineComponent, defineSSRCustomElement, watch } from "vue";
// 导入ref
import { reactive, ref, computed } from "vue";
export default defineComponent({
  name: "App",
  // 组合式API入口

  setup() {
    // 定义参数
    let person = reactive({ name: "张三", age: 30 });
    const newPerson = { name: "李四", age: 50 };
    const onClickHandler = () => {
      for (const attr in newPerson) {
        person[attr] = newPerson[attr];
      }
    };

    // computed
    const num = ref(10);
    const result = computed(() => num.value * 2);
    //#region

    // defineSSRCustomElement
    //#endregion
    // 搜索名字
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
    const search = ref("");
    const filterNames = computed(() =>
      names.value.filter((x) => x.includes(search.value))
    );
    const text = ref("");
    watch(text, (current, pervious) => {
      console.log(current);
      console.log(pervious);
    });

    const personDome1 = ref({ name: "zhangsan", age: { now: "20" } });
    const changeDome1 = () => {
      personDome1.value.name = "freelaeder";
      personDome1.value.age.now = "22";
    };
    watch(
      () => personDome1.value.age.now,
      (current) => {
        console.log(current, "()=>personDome1.value.age.now");
      }
    );
    // 个人理解 （） => 指向具体的值，返回的参数就是最新的值，具体到一个值
    // 如果是一下这种方法， 会获取该属性下所有的值， 直接后面直接 .
    watch(personDome1.value, (current) => {
      console.log(current.age.now, "personDome1.value");
    });
    // const personDome2 = ref({})

    return {
      person,
      onClickHandler,
      result,
      search,
      filterNames,
      text,
      personDome1,
      changeDome1,
    };
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
