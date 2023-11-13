<template>
  <div>
    <InputTodo @add-todo="addTodo"/>
    <TodoList @toggle-completed="toggleCompleted" @delete-todo="deleteTodo" :todoList="todoList"/>
  </div>
</template>

<script>
import InputTodo from './components/InputTodo.vue';
import TodoList from './components/TodoList.vue';

  let ts = new Date().getTime();

  export default {
    name: "App",
    data() {
        return {
            todoList: [
                {id : ts, todo:"H", completed: false},
                {id : ts+1, todo:"g", completed: false},
                {id : ts+2, todo:"k", completed: true},
                {id : ts+3, todo:"o", completed: false}
            ]
        };
    },
    methods: {
        addTodo(todo) {
            this.todoList.push(todo);
        },
        deleteTodo(id) {
            this.todoList = this.todoList.filter(todo => todo.id !== id);
        },
        toggleCompleted(id) {
            let index = this.todoList.findIndex(todo => todo.id === id);
            this.todoList[index].completed = !this.todoList[index].completed;
        }
    },
    components: { InputTodo, TodoList }
}
</script>

<style scoped>

</style>