<!-- src/components/TodoForm.vue -->
<template>
    <div class="todo-form">
      <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Tambahkan List" />
      <button class="add-button" @click="addTodo">Add</button>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  import { useTodoStore } from '../stores/todoStore';
  
  export default {
    setup() {
      const todoStore = useTodoStore();
      const newTodo = ref('');
  
      const addTodo = () => {
        if (newTodo.value.trim() !== '') {
          todoStore.addTodo({
            id: Date.now(),
            text: newTodo.value,
            completed: false,
          });
          newTodo.value = '';
        }
      };
  
      return {
        newTodo,
        addTodo,
      };
    },
  };
  </script>
  
  <style scoped>
  .todo-form {
    display: flex;
    justify-content: center;
    margin-bottom: 20px;
  }
  
  .todo-form input {
    padding: 10px;
    font-size: 16px;
    border: 1px solid #ccc;
    border-radius: 4px;
    flex-grow: 1;
    margin-right: 10px;
  }
  
  .add-button {
    padding: 10px 20px;
    font-size: 16px;
    background: #4caf50;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: background 0.3s;
  }
  
  .add-button:hover {
    background: #45a049;
  }
  </style>
  