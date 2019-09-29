<template>
  <div id="app">
    <Header />
    <Addtodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Header from './components/layout/Header';
import Todos from './components/Todos';
import Addtodo from './components/Addtodo';
import axios from 'axios';

export default {
  name: 'app',
  components: {
    Header,
    Todos,
    Addtodo
  },
  data() {
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => {
        todo.id !== id
      });
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    },
    //runs right away. like compenentmounted
    created() {
      //axios is a http library to make requests..can use fetch api
      axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err))
    }
  }
}
</script>


<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4 rem;
  }

  .btn {
    display: inline-block;
    border: none;
    background-color: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover {
    background-color: #666;
  }
</style>
