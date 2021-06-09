<template>
    <div>
      <ul class="list-group">
        <TodoItem
          v-for="todo of todos"
          v-bind:todo="todo"
          v-bind:key="todo.id"
          @remove-todo="removeTodo"
        />
      </ul>
    </div>
</template>

<script>
  import TodoItem from "@/components/TodoItem"
  export default {
    props: [
      'todos'
    ],
    components: {
      TodoItem
    },
    methods: {
      removeTodo(id) {
        this.$emit('remove-todo', id)
      }
    }
  }
</script>
