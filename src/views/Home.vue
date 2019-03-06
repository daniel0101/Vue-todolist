<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteItem"/>
  </div>
</template>

<script>
import Todos from '../components/Todos';
import AddTodo from '../components/AddTodo';
import axios from 'axios';
export default {
  name: 'app',
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: [
        
      ]
    }
  },
  methods: {
    deleteItem(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(() => this.todos = this.todos.filter(item =>item.id !== id))
      .catch(err => alert(err));      
    },
    addTodo(todo) {
      // this.todos = this.todos.push(todo);
      const {title,completed} = todo;
      //use fetch API to post new variable
      // var config = {
      //   method: 'POST',
      //    headers: {
      //       "Content-Type": "application/json",
      //   },
      //   body: JSON.stringify({title,completed}),
      // }
      // fetch('https://jsonplaceholder.typicode.com/todos',config)
      // .then(response => response.json())
      // .then((response) => {
      //   this.todos = [...this.todos, response];
      // })
      // .catch(err => alert(err));
      axios.post('https://jsonplaceholder.typicode.com/todos',{title,completed})
      .then(response => this.todos = [...this.todos, response.data])
      .catch(err => alert(err));
    },
    fetchTodos(){
      const url = 'https://jsonplaceholder.typicode.com/todos?_limit=10';
      axios.get(url)
      .then((response) => {
        this.todos = response.data;
      })
      .catch(err => alert(err));
    }
  },
  created(){
    this.fetchTodos();
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
    border: none;
    background: #555;
    color: #FFF;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover {
    background: #777;
  }

</style>

