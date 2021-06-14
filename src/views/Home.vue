<template>
<div id="app">
  <add-todo v-on:add-todo="addTodo"></add-todo>
  <Todos :todos="todos" v-on:del-todo="deleteToDo"/>
</div>
</template>

<script>
import Todos from '../components/Todos';
import AddTodo from '../components/AddTodo.vue'
import axios from 'axios'

export default {
  name: 'Home',
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: []
    }
  },
  methods: {
    deleteToDo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`).then(res => {this.todos = this.todos.filter(todo => todo.id !== id); return res})
      .catch(err => console.log(err))
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos',{
        title,
        completed
      }).then(res => this.todos = [...this.todos, res.data])
      .catch(err => console.log(err))
    }
  },
  
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10').then(res => this.todos = res.data).catch(err => console.log(err))
  },
}
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  body {
    font-family: Arial, Helvetica, sans-serif;
    font-size: 30px;
  }
</style>
