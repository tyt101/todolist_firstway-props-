<template>
<li>
    <label>
    <input type="checkbox"
    v-model="li.isDone"
    />
    <span>{{li.name}}</span>
    </label>
    <button class="btn btn-danger"
    @click="deleteTask(li.id)"
    >删除</button>
</li>
</template>

<script>
export default {
    name:'todo-list',
    props:['li','deleteTaskF'],
    methods: {
        deleteTask(id){
            this.deleteTaskF(id)
        }
    },
}
</script>

<style scoped>
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
li:hover{
    background-color: #ccc;
}
li:hover button{
    display: block;
}
li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}
</style>