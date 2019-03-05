<template>
  <div id="app">
    <Header/>
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteItem"/>
  </div>
</template>

<script>
import Header from './components/layouts/Header';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';
export default {
  name: 'app',
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: 'Make My Bed',
          completed: false
        },
        {
          id: 2,
          title: 'Learn Vue',
          completed: true
        },
        {
          id: 3,
          title: 'German Classes',
          completed: false
        }
      ]
    }
  },
  methods: {
    deleteItem(id) {
      this.todos = this.todos.filter(item =>item.id !== id);
    },
    addTodo(todo) {
      // this.todos = this.todos.push(todo);
      this.todos = [...this.todos, todo];
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
