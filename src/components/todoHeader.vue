<template>
  <div class="todo-header">
    <input
      type="text"
      placeholder="what needs to be done ?"
      v-model="title"
      @keyup.enter="add"
    />
  </div>
</template>

<script>
import { nanoid } from "nanoid";
export default {
  props: ["addTodo"],
  data() {
    return {
      title: "",
    };
  },
  methods: {
    add() {
      // 校验数据 确保数据不为空
      if (this.title.trim()) {
        //将用户输入的包装成一个对象
        const TodoObj = { id: nanoid(), title: this.title, done: false };
        console.log(TodoObj);
        //通知父组件添加一个数据
        this.addTodo(TodoObj);
        this.title = ""; //添加完后需要清空
      } else {
        alert("你咋这么皮，输入不能为空，添加失败");
        return;
      }
    },
  },
};
</script>

<style lang="less" scoped>
.todo-header input {
  width: 90%;
  margin-left: 40px;
  // width: 500px;
  height: 28px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 4px 7px;
}
input::placeholder {
  color: #ccc;
  font-style: italic;
  opacity: 0.5;
  padding: 20px;
  font-size: 20px;
}
.todo-header input:focus {
  outline: none;
  border-color: rgba(82, 168, 236, 0.8);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075),
    0 0 8px rgba(82, 168, 236, 0.6);
}
</style>
