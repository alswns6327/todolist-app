<template>
    <div>
        <TodoListItem v-for="todo in todoList" :key="todo.id" :todo="todo"/>
    </div>
</template>

<script>
import TodoListItem from './TodoListItem.vue';

    export default {
    name: "TodoList",
    components: { TodoListItem },
    props : ["todoList"]
}
</script>

<style scoped>

</style>