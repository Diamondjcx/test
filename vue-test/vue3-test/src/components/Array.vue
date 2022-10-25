<template>
  <div>
    {{ arr }}
  </div>
  <div>
    <button @click="handleAddAttr">数组每项增加属性</button>
  </div>
  <div>
    <button @click="handleChangeAttr">改变数组name属性</button>
  </div>
  <div>
    <button @click="handleChangePush">数组push新属性</button>
  </div>
  <div>
    <button @click="handleChangeSlice">数组slice</button>
  </div>
  <div>
    <button @click="handleChangeSplice">数组splice</button>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { provices } from "../utils/constant";
const arr = ref([
  {
    name: "张三",
    age: 10,
  },
  {
    name: "李四",
    age: 20,
  },
]);
const handleAddAttr = () => {
  arr.value.forEach((val) => {
    val["check"] = true;
  });
};
const handleChangeAttr = (val) => {
  arr.value[0]["name"] = "李四";
};
const handleChangePush = () => {
  arr.value.push({ hair: "long" });
};
const handleChangeSlice = () => {
  arr.value = arr.value.slice(1);
};
const handleChangeSplice = () => {
  arr.value.splice(1);
};
</script>

<style lang="scss" scoped>
</style>