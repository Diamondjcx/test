<template>
  <div>
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

    <div>
      {{ obj }}
    </div>
    <div>
      <button @click="handleObjectAddAttr">对象新增属性</button>
    </div>
  </div>
</template>

<script>
// push()
// pop()
// shift()
// unshift()
// splice()
// sort()
// reverse()
// this.$set
// Object.assign({},this.myObject,{newkey,newval})
// this.$forceUpdate
// 响应式原理

import { provices } from "../utils/constant";
export default {
  data() {
    return {
      provices,
      arr: [
        {
          name: "张三",
          age: 10,
        },
        {
          name: "李四",
          age: 20,
        },
      ],
      obj: {
        name: "1111",
      },
    };
  },
  created() {
    console.log("this.arr", this.arr);
  },
  methods: {
    handleAddAttr() {
      this.arr.forEach((val) => {
        // val["check"] = true;
        this.$set(val, "check", true);
        // val = Object.assign({}, val, { check: true });
      });
      console.log("this.arr", this.arr);
      // this.$forceUpdate();

      // 1. 使用set
      // 2. 使用this.$forceUpdate()
      // vue无法探测普通的新增property属性  this.myObject.newProperty = 'hi'
    },
    handleChangeAttr() {
      this.arr[0].name = "李四";
      // this.arr[0] = 111 // 不生效
    },
    handleChangePush() {
      this.arr.push({ hair: "long" });
    },
    handleChangeSlice() {
      this.arr = this.arr.slice(1);
    },
    handleChangeSplice() {
      this.arr.splice(1);
    },
    /**
     * 对象新增属性 变成响应式
     */
    handleObjectAddAttr() {
      // this.$set(this.obj, "age", 100);
      this.obj = Object.assign({}, this.obj, { age: 1000 });
    },
  },
};
</script>

<style lang="scss" scoped>
</style>