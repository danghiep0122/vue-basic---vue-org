<script>
let id = 0;
export default {
  data() {
    return {
      newTodo: "",
      hideCompleted: false,
      todos: [
        { id: id++, text: "Learn HTML", done: true },
        { id: id++, text: "Learn CSS", done: false },
        { id: id++, text: "Learn Javascript", done: false },
      ],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== "") {
        this.todos.push({ id: id++, text: this.newTodo });
        this.newTodo = "";
      }
    },
    removeTodo(todo) {
      this.todos = this.todos.filter((target) => target !== todo);
    },
  },
  computed: {
    filteredTodos() {
      return this.hideCompleted
        ? this.todos.filter((t) => !t.done)
        : this.todos;
    },
  },
};
</script>

<template>
  <div class="todo-app">
    <form class="input" @submit.prevent="addTodo">
      <input class="green" v-model="newTodo" />
      <button>Add</button>
    </form>
    <ul class="list-item">
      <li v-for="todo in filteredTodos" :key="todo.id">
        <input type="checkbox" v-model="todo.done" />
        <span class="list-title" :class="{ done: todo.done }">
          {{ todo.text }}
        </span>
        <button class="remove-todo-btn" @click="removeTodo(todo)">✖</button>
      </li>
    </ul>
    <button @click="hideCompleted = !hideCompleted">
      {{ hideCompleted ? "Show All" : "Hide Completed" }}
    </button>
  </div>
</template>

<style scoped>
.todo-app {
  display: flex;
  flex-direction: column;
}

.input {
  display: flex;
}

.input input {
  padding: 0.4rem;
  flex: 1;
  outline: none;
  box-shadow: hsla(160, 100%, 37%, 1) 0 0 10px;
  border-bottom-left-radius: 0.4rem;
  border-top-left-radius: 0.4rem;
  border-color: var(--primary-color);
}

.input button {
  padding: 0 1.8rem;
  border-color: var(--primary-color);
  box-shadow: var(--primary-color) 0 0 10px;
  border-bottom-right-radius: 0.4rem;
  border-top-right-radius: 0.4rem;
  background-color: var(--primary-color);
  color: #111;
  cursor: pointer;
}
.list-item {
  padding: 0;
  margin-top: 1rem;
}

li {
  display: flex;
  justify-content: flex-start;
  padding: 0.4rem;
  border-bottom: 1px solid rgba(0, 189, 126, 0.4);
}

.list-title {
  flex: 1;
  margin: 0 1rem;
  color: var(--primary-color);
}

.list-title.done {
  text-decoration: line-through;
  color: var(--vt-c-text-dark-2);
}

.remove-todo-btn {
  cursor: pointer;
  background-color: #e63946;
  color: #f1faee;
}
</style>
