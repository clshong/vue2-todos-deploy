<template>
  <div class="todo-footer" v-show="this.total">
    <label>
      <input type="checkbox"  v-model='ischeckAll'/>
    </label>
    <span> <span>已完成{{completed}}</span> / 全部{{total}} </span>
    <button class="btn btn-danger" @click="cleartDone">Clear completed</button>
  </div>
</template>

<script>
export default {
props:['TodoList','checkAllTodos','clearAllTodo'],
computed:{
  completed(){
  return  this.TodoList.reduce((pre,cur)=> pre + (cur.done ? 1 : 0),0)
  },
  total(){
    return this.TodoList.length
  },
ischeckAll:{
  get(){
    return this.completed === this.total && this.total > 0 
  },
  set(value){
    this.checkAllTodos(value)
  }
}

},
methods:{
  cleartDone(){
    if(confirm('确认事情完成度在删除')){
      this.clearAllTodo()
    }
    
  }
}

};
</script>

<style lang="less" scoped>
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}

.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}

.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}

.todo-footer button {
  float: right;
  margin-top: 5px;
}
</style>
