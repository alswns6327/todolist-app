<template>
    <div class="row">
        <div class="col">
            <div class="list-group">
                <TodoListItem 
                    @delete-todo="$emit('delete-todo', $event)" 
                    @toggle-completed="$emit('toggle-completed', $event)" 
                    v-for="todoItem in todoList" :key="todoItem.id" :todoItem="todoItem"
                />
            </div>
        </div>
    </div>
</template>

<script setup>
    import TodoListItem from './TodoListItem.vue';

    const props = defineProps({
        todoList : {type : Array, required : true}
    });
    
    const emit = defineEmits(['delete-todo', 'toggle-completed'])
</script>

<style scoped>

</style>