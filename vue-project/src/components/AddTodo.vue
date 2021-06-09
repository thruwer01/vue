<template>
  <input 
    type="text" 
    class="form-control"
    placeholder="Введите название задачи"
    v-model="addTodoTitle"
    @keypress.enter="addTodo"
  >
</template>


<script>
export default {
  data() {
    return {
      addTodoTitle: ''
    }
  },
  methods: {
    addTodo() {
      const newTodo = {
        id: Date.now(),
        title: this.addTodoTitle,
        completed: false
      }
      this.$emit('add-todo', newTodo);
      this.addTodoTitle = ''
    }
  }
}
</script>