<template>
  <div>
    <form @submit="addTodo">
      <input type="text" v-model="title" name="title" placeholder="Add Todo...">
      <input type="submit" value="Submit" class="btn">
    </form>
  </div>
</template>

<script>
// import {v4 as uuidv4} from 'uuid';
// import { v4 as uuidv4 } from 'uuid';


export default {
  name: 'AddTodo',
  data() {
    return {
      title: ''
    }
  },
  methods: {
    addTodo(event) {
      
      event.preventDefault();
      const newTodo = {
        title: this.title,
        completed: false
      }
      //Send to parent
      this.$emit('add-todo', newTodo);
      this.title = ''
      // console.log(myuuid)
    }
  }
}
</script>

<style scoped>
form {
  display: flex;
}
input[type="text"] {
  flex: 10;
  border: none;
  background-color: rgb(179, 179, 179);
  height: 50px;
  padding: 20px;
  font-size: 20px;
}
input[type="text"]:focus {
  outline: none;
}
input[type="submit"]:focus {
  outline: none;
}
input[type="submit"]:hover {
  background-color: rgb(211 64 64 / 74%);
}
input {
  caret-color: rgb(211 64 64);
}

input[type="submit"] {
  flex: 2;
  border: none;
  background-color: rgb(211 64 64);
  color: #fff;
  font-size: 20px;
  cursor: pointer;
}
</style>