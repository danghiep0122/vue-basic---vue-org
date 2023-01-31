<script>
export default {
  data() {
    return {
      todoId: 1,
      todoData: null,
    };
  },
  methods: {
    async fetchTodo() {
      const res = await fetch(
        `https://jsonplaceholder.typicode.com/todos/${this.todoId}`
      );

      this.todoData = await res.json();
    },
  },
  mounted() {
    this.fetchTodo();
  },
  watch: {
    todoId() {
      this.fetchTodo();
    },
  },
};
</script>

<template>
  <div class="fetch-todo">
    <h4>
      <span class="title">Todo id:</span>
      {{ todoId }}
    </h4>
    <p v-if="!todoData">Loading ...</p>
    <div v-else class="todo-data">
      <h3>
        <span class="title">Todo title: </span>
        {{ todoData.title }}
      </h3>
    </div>
    <button class="btn" @click="todoId++">Click to next Todo</button>
  </div>
</template>

<style scoped>
.title {
  color: var(--primary-color);
  font-weight: 600;
}

.btn {
  background-color: var(--primary-color);
  color: #f4f4f4;
  padding: 1rem;
  border-radius: 0.6rem;
  cursor: pointer;
}
</style>
