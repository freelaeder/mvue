<template>
  <div></div>
  <hr />
  <h2>{{ name }}{{ age }}</h2>

  <button @click="onChangeName">change name age</button>

  <hr />
  <h6>{{ refAge }} {{ refName }}</h6>
  <button @click="refChangeNameAndAge">change ref name age</button>

  <!-- reactive -->
  <hr />
  <h6>{{ reactivePerson.age }} {{ reactivePerson.name }}</h6>
  <button @click="rChangePerson">change ref name age</button>
</template>

<script lang="ts">
import { defineComponent } from "vue";
// 导入ref
import { ref, reactive } from "vue";
export default defineComponent({
  name: "App",
  // 组合式API入口

  setup() {
    // 返回值
    console.log(this, "setup");
    let name = "freelaeder";
    let age = 20;

    const refName = ref("张三");
    const refAge = ref(44);

    const refChangeNameAndAge = () => {
      refName.value = "zhangsansan";
      refAge.value = 33;
    };

    const reactivePerson = reactive({ name: "r张丹", age: 99 });
    const rChangePerson = () => {
      reactivePerson.name = "new 张丹";
      reactivePerson.age = 9;
    };

    /**注意：在 setup 方法中声明的变量虽然可以在模板中显示，
     * 但它不是响应式数据，就是说当数据发生变化后视图不会更新。 */
    const onChangeName = () => {
      name = "free";
      age = 22;
    };

    return {
      name,
      age,
      onChangeName,
      refName,
      refAge,
      refChangeNameAndAge,
      reactivePerson,
      rChangePerson,
    };
  },
  beforeCreate() {
    console.log(this, "beforecreate");
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
