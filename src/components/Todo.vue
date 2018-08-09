<template>
  <div class='ui centered card'>
    <div class='ui content'>
      <div v-show="!isEditing">
        <i class='right floated trash icon' v-on:click="deleteTodo(todo)"></i>
        <i class='right floated edit icon' v-on:click="editTodo(todo)"></i>
        <input type="checkbox" id="checkbox" v-model="todo.done" v-on:click="toggleListing(todo)" />
        <label>
          {{ todo.title }}
        </label>
      </div>
      <div class="ui form" v-show="isEditing">
        <div class="field">
          <input type="text" id="editTitleText" v-model.lazy="todo.title" />
        </div>
      </div>
    </div>
  </div>
</template>

<script type="text/javascript">
export default {
  props: ['todo'],
  data: function () {
    return {
      isEditing: false
    }
  },
  methods: {
    editTodo: function (todo) {
      // this.$emit('edit-todo')
      // Remove delete and checkbox in the meantime (v-show)?
      this.isEditing = true
    },
    modifyTitle: function (todo) {
      const title = this.titl
      this.$emit('modify-todo', todo, title)
    },
    deleteTodo: function (todo) {
      this.$emit('delete-todo', todo)
    },
    toggleListing: function (todo) {
      this.$emit('toggle-listing', todo)
    }
  }
}
</script>
