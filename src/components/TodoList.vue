<template>
  <div>
    <todo
      v-for="todo in todos"
      v-bind:todo="todo"
      v-bind:key="todo.title"
      v-on:delete-todo="deleteTodo"
      v-on:toggle-listing="toggleListing"
      v-on:modify-todo="modifyTodo"
    ></todo>
  </div>
</template>

<script type = "text/javascript">
import Todo from './Todo'

export default {
  props: ['todos'],
  components: {
    Todo
  },
  methods: {
    deleteTodo: function (todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos.splice(todoIndex, 1)
    },
    modifyTodo: function (todo, newTitle) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos[todoIndex].title = newTitle
    },
    toggleListing: function (todo) {
      const todoIndex = this.todos.indexOf(todo)
      if (todo.done) {
        this.todos.unshift(this.todos.splice(todoIndex, 1)[0])
      } else {
        this.todos.push(this.todos.splice(todoIndex, 1)[0])
      }
    }
  }
}
</script>

<style>
</style>
