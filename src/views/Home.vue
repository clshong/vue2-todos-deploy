<template>
  <div class="home">
    <div class="logo">
      <p>todos</p>
      <img alt="Vue logo" src="../assets/logo.png" />
    </div>
    <TodoHeader 
    :addTodo="addTodo" 
    />
    <TodoList 
    :todoObj="TodoList" 
    :checkTodo="checkTodo"
    :delTodo ='delTodo'
    />
    <TodoFooter 
    :TodoList="TodoList"
    :checkAllTodos = 'checkAllTodos'
    :clearAllTodo="clearAllTodo"
    />
  </div>
</template>

<script>
import TodoHeader from "@/components/todoHeader";
import TodoList from "@/components/todoList";
import TodoFooter from "@/components/todoFooter";

export default {
  name: "Home",
  components: { TodoHeader, TodoList, TodoFooter },
  data() {
    return {
      TodoList: [],
    };
  },
  methods:{
    //添加一个事项
    addTodo(item){
      this.TodoList.push(item)
    },
    //勾选或者未勾选
    checkTodo(id){
      this.TodoList.forEach(todo => {
        if(todo.id === id) todo.done = !todo.done
      }
      )
    },
    // 删除一个元素
    delTodo(id){
      this.TodoList = this.TodoList.filter(v => v.id !== id )
    },
    //勾选or反选
    checkAllTodos(done){
      this.TodoList.forEach(todo =>{
        todo.done = done
      })
    },
    // 清空已经完成
    clearAllTodo(){
      this.TodoList = this.TodoList.filter(v => !v.done)
    }
  }
};
</script>

<style lang="less">
body {
  background: #fff;
}
.btn {
  display: inline-block;
  padding: 4px 12px;
  margin-bottom: 0;
  font-size: 14px;
  line-height: 20px;
  text-align: center;
  vertical-align: middle;
  cursor: pointer;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2),
    0 1px 2px rgba(0, 0, 0, 0.05);
  border-radius: 4px;
}

.btn-danger {
  color: #fff;
  background-color: #da4f49;
  border: 1px solid #bd362f;
}

.btn-danger:hover {
  color: #fff;
  background-color: #bd362f;
}

.btn:focus {
  outline: none;
}

.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
.home {
  width: 60vw;
  margin: 4rem auto;
  border: 1px solid #ddd;
  padding: 1rem;
  box-shadow: 0.6rem 0.6rem 2rem #ccc;
  .logo {
    display: flex;
    align-items: center;
    justify-content: center;
    p {
      color: #c94545;
      opacity: 0.6;
      margin-right: 1rem;
    }
    img {
      width: 2rem;
      height: 2rem;
    }
  }
}
</style>
