<template>
<div class="todo-item" :class="{'is-complete' : todo.completed}">
    <p>
      <input type="checkbox" v-on:change="markComplete(todo.completed)">
      {{ todo.title }}</p>
      <button @click="$emit('del-todo', todo.id)" class="del">
        <img :src="path" alt="">
      </button>
  </div>
</template>


<script>

export default {
  name: "TodoItem",
  props:['todo', "todo_prop"],
  data() {
    return {
      todos : this.todo,
      path: require('../assets/close.png')
    }
  },
  methods: {
   markComplete(isComplete) {
     this.todos.completed =! isComplete
     }
  }
}
</script>

<style scoped>
  .todo-item {
    background-color: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
    display: flex;
    justify-content: space-between;
    transition: all .1s ease-in-out;
  }
  .is-complete {
    text-decoration: line-through;
    color: rgb(180, 180, 180);
  }
  .del {
    /* background-color: #808080; */
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 19%;
    cursor: pointer;
    float: right;
    /* width: 35px; */
    /* height: 34px; */
    /* line-height: 22px; */
    font-size: 22px;
    transition: all .1s ease-in-out;
  }
  img {
    width: 18px;

  }
</style>
