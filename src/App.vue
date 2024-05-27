<template>
  <div id="app" class="container">
    <h1 class="my-4">To-Do List</h1>
    <div class="input-group mb-3">
      <input
        v-model="newTodo"
        @keyup.enter="addTodo"
        type="text"
        class="form-control"
        placeholder="Add a new task"
      />
      <button @click="addTodo" class="btn btn-primary" type="button">Add</button>
    </div>
    <ul class="list-group">
      <li
        v-for="(todo, index) in todos"
        :key="index"
        class="list-group-item d-flex justify-content-between align-items-center"
      >
        <div>
          <input type="checkbox" v-model="todo.completed" class="form-check-input me-1" />
          <span :class="{ 'text-decoration-line-through': todo.completed }">
            {{ todo.text }}
          </span>
        </div>
        <button @click="removeTodo(index)" class="btn btn-danger btn-sm">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: '',
      todos: []
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== '') {
        this.todos.push({ text: this.newTodo, completed: false });
        this.newTodo = '';
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    }
  }
};
</script>

<style scoped>
.container {
  max-width: 600px;
  margin: 0 auto;
}
</style>
