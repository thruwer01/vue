<template>
  <div>
    <div class="container mt-5">
      <div class="title mb-3">
        <h1 class="fw-bold">Задачи</h1>
      </div>
      <div class="col-12">
        <AddTodo 
          @add-todo="addTodo"
        />
        <div>
          <hr/>
          <TodoList 
            v-if="todos.length > 0"
            v-bind:todos="todos" 
            @remove-todo="removeTodo"
          />
          <div 
            class="mt-3 fw-bold"
            v-else
            >
            Нет запланированных задач!
          </div>
        </div>
        </div>
    </div>
  </div>
</template>



<script>
import TodoList from "@/components/TodoList"
import AddTodo from "@/components/AddTodo"
export default {
  data() {
    return {
      todos: []
    }
  },
  components: {
    TodoList, AddTodo
  },
  async mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos/?_limit=5')
    .then(response => response.json())
    .then(json => {
      this.todos = json;
    })
  },
  methods: {
    removeTodo (id) {
      this.todos = this.todos.filter(t => t.id !== id);
    },
    addTodo (newTodo) {
      this.todos.push(newTodo);
    }
  }
}
</script>
