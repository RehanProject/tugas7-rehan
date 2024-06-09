<!-- src/components/TodoList.vue -->
<template>
    <div class="todo-list">
      <ul>
        <li v-for="todo in todos" :key="todo.id" :class="{ completed: todo.completed }">
          <span @click="toggleTodo(todo.id)">
            {{ todo.text }}
          </span>
          <button class="delete-button" @click="removeTodo(todo.id)">Delete</button>
        </li>
      </ul>
      <p>List Yang Sudah Selesai : {{ incompleteTodosCount }}</p>
    </div>
  </template>
  
  <script>
  import { useTodoStore } from '../stores/todoStore';
  import { computed } from 'vue';
  
  export default {
    setup() {
      const todoStore = useTodoStore();
      const todos = computed(() => todoStore.todos);
      const incompleteTodosCount = computed(() => todoStore.incompleteTodosCount);
  
      const toggleTodo = (id) => {
        todoStore.toggleTodo(id);
      };
  
      const removeTodo = (id) => {
        todoStore.removeTodo(id);
      };
  
      return {
        todos,
        toggleTodo,
        removeTodo,
        incompleteTodosCount,
      };
    },
  };
  </script>
  
  <style scoped>
  .todo-list ul {
    list-style: none;
    padding: 0;
  }
  
  .todo-list li {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    border-bottom: 1px solid #ddd;
    transition: background 0.3s;
  }
  
  .todo-list li:hover {
    background: #f1f1f1;
  }
  
  .todo-list li span {
    flex-grow: 1;
    cursor: pointer;
    transition: color 0.3s;
  }
  
  .todo-list li span.completed {
    text-decoration: line-through;
    color: grey;
  }
  
  .delete-button {
    background: #ff4d4d;
    color: white;
    border: none;
    padding: 5px 10px;
    border-radius: 4px;
    cursor: pointer;
    transition: background 0.3s;
  }
  
  .delete-button:hover {
    background: #ff3333;
  }
  
  p {
    margin-top: 20px;
    font-weight: bold;
  }
  </style>
  