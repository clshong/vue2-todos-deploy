<template>
    <ul class="todo-main">
      <TodoItem 
      v-for=" todo in todoObj" 
      :key="todo.id" 
      :todoObj="todo" 
      :checkTodo = 'checkTodo'
      :delTodo="delTodo"
      />
      </ul>    
</template>
<script>
import TodoItem from './todoItem.vue';
  export default {
    components: { TodoItem },
    props:['todoObj','checkTodo','delTodo']
}
</script>

<style lang="less" scoped>
.todo-main {
  margin-left: 0px;
  // border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
</style>