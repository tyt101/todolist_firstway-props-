<template>
<div id="app">
  <TodoHeader :getTask="getTask"></TodoHeader>
  <TodoMain :list="list" :deleteTaskF="deleteTaskF"></TodoMain>
  <TodoFooter :list="list" :changeTasks='changeTasks' :clearAll='clearAll'></TodoFooter>
</div>
</template>

<script>
import TodoHeader from './components/TodoHeader'
import TodoMain from './components/TodoMain'
import TodoFooter from './components/TodoFooter'
export default {
  name: 'App',
  components: {
    TodoHeader,
    TodoMain,
    TodoFooter
  },
  data() {
    return {
      list:[
        {id:1,name:'吃饭',isDone:true},
        {id:2,name:'睡觉',isDone:false},
        {id:3,name:'打豆豆',isDone:true},
      ]
    }
  },
  methods: {
    getTask(task){
      this.list.push(task)
    },
    deleteTaskF(taskId){
      this.list = this.list.filter(task=>{
          return task.id!=taskId
      })
    },
    changeTasks(ischeck){
      this.list.forEach(li=>{
        li.isDone=ischeck
      })
    },
    clearAll(){
      this.list=this.list.filter(li=>{
        return !li.isDone
      })
    }
  },
}
</script>

<style >

body {
  background: #fff;
}
#app{
  width:576px;
  margin:0 auto;
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
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 1px 2px rgba(0, 0, 0, 0.05);
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
</style>
