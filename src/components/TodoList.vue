<template>
    <div>
        <div class="row">
            <div class="col-12">
                <p class="display-3">Hey there!! Your Todo is waiting</p>
            </div>
        </div>

        <div class="row">
            <p>Input text here</p>
        </div>
        <div class="row">
            <div class="col-12 col-lg-6">
                <ul class="list-group">
                    <Todo v-for="(todo, index) in todos" 
                    :key="index" 
                    :todoName="todo.todoName"
                    :completed="todo.completed"
                    @on-delete="deleteTodo(todo)"
                    @on-toggle="toggleTodo(todo)"
                    @on-edit="editTodo(todo , $event )" />
                </ul>
            </div>
        </div>
    </div>
    
</template>

<script>
import Todo from './todo.vue';
export default {
    components: {
        Todo
    },
    data(){
        return {
            todos : [{todoName: "Learn Vue" , completed : false},
                    {todoName: "Brush up your Apex concepts" , completed : true},
                    {todoName: "Code Code Code" , completed : false},]
        }
    },
    
    methods: {
        addTodo(newTodo){
            this.todos.push({
                todoName : newTodo,
                completed : false
            });
        },

        toggleTodo(todo){
            todo.completed = !todo.completed
        },

        editTodo(todo , newTodoName){
            todo.todoName = newTodoName
        },

        deleteTodo(deleteTodo){
            this.todos = this.todos.filter( todo => todo !== deleteTodo);
        },
    }//methods_ends
};//export_default_ends

</script>

<style>

</style>