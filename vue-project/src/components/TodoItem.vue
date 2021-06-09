<template>
  <li
    class="list-group-item d-flex align-items-center justify-content-between"
  >
    <input 
      type="checkbox"
      v-model="todo.completed"
    >
    <h5
      v-bind:class="{done: todo.completed}"
    >
      {{ todo.title }}
    </h5>
    <button 
      class="btn btn-danger"
      @click="$emit('remove-todo', todo.id)"
    >
      Удалить
    </button>
  </li>
</template>

<script>
  export default {
    props: [
      'todo'
    ]
  }
</script>

<style scoped>
  .done {
    text-decoration: line-through ;
  }
</style>