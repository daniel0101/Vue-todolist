<template>
  <div id="app">
    <Header/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteItem"/>
  </div>
</template>

<script>
import Header from './components/layouts/Header';
import Todos from './components/Todos';
export default {
  name: 'app',
  components: {
    Todos,Header
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
      this.todos = this.todos.filter(item =>{ item.id !== id});
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

</style>
