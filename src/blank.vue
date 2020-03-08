<template>
  <div id="app">
    <Header />
    <AddTask v-on:add-task="addTask"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Header from './components/layout/Header';
import Todos from './components/Todos';
import AddTask from './components/AddTask';
import axios from 'axios';

export default {
  name: 'app',
  components: {
    Header,
    Todos,
    AddTask
  },
  data() {
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(this.todos = this.todos.filter(todo => todo.id !== id))  // This uses the filter() to delete the Task
        .catch(error => console.log(error));
    },
    addTask(newTask) {
      const { title, completed } = newTask;

      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
        .then(response => this.todos = [...this.todos, response.data])
        .catch(error => console.log(error)); 
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(response => this.todos = response.data)
      .catch(error => console.log(error));
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
    line-height: 1.4;
  }

  .btn {
    display: inline-block;
    border-color: #e1e1e1;
    background: #FAFAFA;
    color: #737581;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover {
    background: #e1e1e1;
  }
</style>
