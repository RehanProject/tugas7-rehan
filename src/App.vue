<!-- src/App.vue -->
<template>
  <div id="app">
    <div class="container">
      <h1>Todo List Saya</h1>
      <TodoForm />
      <TodoList />
    </div>
  </div>
</template>

<script>
import TodoForm from './components/TodoForm.vue';
import TodoList from './components/TodoList.vue';

export default {
  components: {
    TodoForm,
    TodoList,
  },
};
</script>

<style scoped>
.container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  background: #a8aba5;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  border-radius: 8px;
  text-align: center;
}

h1 {
  color: #333;
  margin-bottom: 20px;
}
</style>
