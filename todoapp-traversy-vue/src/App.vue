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

export default {
  name: 'app',
  components: {
    Header,
    Todos,
    Addtodo
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Feed Dogs",
          completed: false
        },
        {
          id: 2,
          title: "Walk Dogs",
          completed: true
        },
        {
          id: 3,
          title: "Treat Dogs",
          completed: false
        }
      ]
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
