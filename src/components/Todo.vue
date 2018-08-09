<template>
  <div class='ui centered card'>
    <div class='ui content'>
      <i class='right floated trash icon' v-on:click="deleteTodo(todo)"></i>
      <input type="checkbox" id="checkbox" v-model="todo.done" v-on:click="toggleListing(todo)" />
      <label>
        {{ todo.title }}
      </label>
    </div>
  </div>
</template>

<script type="text/javascript">
export default {
  props: ['todo'],
  methods: {
    deleteTodo: function (todo) {
      this.$emit('delete-todo', todo)
    },
    toggleListing: function (todo) {
      this.$emit('toggle-listing', todo)
    }
  }
}
</script>
