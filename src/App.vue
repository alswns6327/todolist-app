<template>
  <div>
    <InputTodo @add-todo="addTodo"/>
    <TodoList @toggle-todo="toggleTodo" @delete-todo="deleteTodo" :todoList="todoList"/>
  </div>
</template>

<script>
import InputTodo from './components/InputTodo.vue';
import TodoList from './components/TodoList.vue';

  export default {
    name: "App",
    data() {
        return {
            todoList: []
        };
    },
    methods: {
        addTodo(todo) {
            this.todoList.push(todo);
        },
        deleteTodo(id) {
            this.todoList = this.todoList.filter(todo => todo.id != id);
        },
        toggleTodo(id) {
            let index = this.todoList.findIndex(todo => todo.id = id);
            this.todoList[index].completed = true;
        }
    },
    components: { InputTodo, TodoList }
}
</script>

<style scoped>

</style>