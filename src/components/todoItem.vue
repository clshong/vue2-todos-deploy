<template>
  <div>
    <li>
      <label>
        <input type="checkbox" :checked='todoObj.done' @click="handercheck(todoObj.id)"/>
        <span>{{todoObj.title}}</span>
      </label>
      <button class="btn btn-danger" @click="handerdel(todoObj.id)">x</button>
    </li>
  </div>
</template>

<script>
export default {
  props:['todoObj','checkTodo','delTodo'],
methods:{
  handercheck(id){
    //根据id修改完成状态
    this.checkTodo(id)
  },
  handerdel(id){
    // 根据id删除元素
    if(confirm('事情完成了吗？')){
      this.delTodo(id)
    }
    
  }
}
};
</script>

<style lang="less" scoped>
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}

li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}

li button {
  float: right;
  display: none;
  margin-top: 3px;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}

li:hover{
  background: #ccc;
}
li:hover button{
  display: block;
}
</style>
