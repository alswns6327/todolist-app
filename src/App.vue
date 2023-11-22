<template>
    <div>
      <InputTodo @add-todo="addTodo"/>
      <TodoList :todoList="state.todoList" @delete-todo="deleteTodo" @toggle-completed="toggleCompleted"/>
    </div>
  </template>
  
  <script setup>
  import { onMounted, reactive } from 'vue';
  import InputTodo from './components/InputTodo.vue';
  import TodoList from './components/TodoList.vue';
    const ts = new Date().getTime();
    const state = reactive({todoList : []});
    onMounted(() => {
        state.todoList.push({id : ts, todo:"H", completed: false});
        state.todoList.push({id : ts+1, todo:"g", completed: false});
        state.todoList.push({id : ts+2, todo:"k", completed: true});
        state.todoList.push({id : ts+3, todo:"o", completed: false});
    });

    const addTodo = (todo) => {
        if(todo.length >= 2){
            state.todoList.push({id : new Date().getTime(), todo : todo, completed : false});
        }
    }

    const deleteTodo = (id) => {
        let index = state.todoList.findIndex(todo => todo.id === id);
        state.todoList.splice(index, 1);
    }

    const toggleCompleted = (id) => {
        let index = state.todoList.findIndex(todo => todo.id === id);
        state.todoList[index].completed = !state.todoList[index].completed;
    }
  </script>
  
  <style scoped>
  
  </style>