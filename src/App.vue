<template>
  <div id="app">
    <create-todo v-on:create-todo="createTodo"></create-todo>
    <todo-list v-bind:todos="todos"></todo-list>
  </div>
</template>

<script>
import TodoList from './components/TodoList'
import CreateTodo from './components/CreateTodo'

export default {
  name: 'App',
  components: {
    TodoList,
    CreateTodo
  },
  data: function () {
    return {
      todos: []
    }
  },
  methods: {
    createTodo: function (title) {
      this.todos.unshift(title)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
