<template>
  <div class='ui basic content center aligned segment'>
    <div class='ui centered card'>
      <div class='content'>
        <div class='field ui action input'>
          <input v-model="titleText" type='text' ref='title' placeholder="e.g. Make dishes" />
          <button class="ui button" v-on:click="sendForm()">Create</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      titleText: ''
    }
  },
  methods: {
    openForm: function () {
      this.isCreating = true
    },
    closeForm: function () {
      this.isCreating = false
    },
    sendForm: function () {
      if (this.titleText.length > 0) {
        const title = this.titleText
        this.$emit('create-todo', {
          title,
          done: false
        })

        this.titleText = ''
      }
    }
  }
}
</script>
