<template>
    <div class="row mb-3">
        <div class="col">
            <div class="input-group">
                <input id="msg" type="text" class="form-control" name="msg"
                    placeholder="목록 입력" v-model.trim="todo"
                    @keyup.enter="addTodoHandler"
                    />
                <button class="btn btn-primary input-group-addon" @click="addTodoHandler">추가</button>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name : "InputTodo",
        data(){
            return{
                todo : ""
            }
        },
        emits : ["add-todo"],
        methods : {
            addTodoHandler(){
                if(this.todo.trim().length >= 3){
                    this.$emit("add-todo", {id : new Date().getTime, todo: this.todo, completed : false});
                    this.todo = "";
                }else{
                    alert("3자 이상 입력");
                }
            }
        }
    }
</script>

<style scoped>

</style>