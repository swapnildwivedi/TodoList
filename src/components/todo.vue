<template>
    <div class="container">
        <li class="d-flex align-items-center list-group-items">
            <button 
            :class="{completed}"
            @click="$emit('on-toggle')"
            class="btn border-0 text-left flex-grow-1">{{todoName}}</button>
            <form @submit.prevent="endEditing()" class="flex-grow-1">
                <input @blur="startEditing()" v-model="newTodoName" type="text" class="form-control"/>
            </form>
            <button @click ="startEditing()" class="btn btn-outline-primary">Edit</button>
            <button @click="$emit('on-delete')" class="btn btn-outline-danger">Delete</button>
        </li>
    </div>
</template>

<script>
export default {
    props:{
        todoName: String,
        completed: Boolean,
    },
    data(){
        return {
            isEditing: false,
            newTodoName : "",
        };
    },
    
    methods:{
        startEditing(){
            if(!this.isEditing){
                this.newTodoName = this.todoName;
                this.isEditing = true;
            }else{
                this.endEditing();
            }
        },
        endEditing(){
            this.isEditing = false;
            this.$emit('on-edit' , this.newTodoName)
        },
    },
}
</script>

<style scoped>
.completed{
    text-decoration: line-through;
}
</style>