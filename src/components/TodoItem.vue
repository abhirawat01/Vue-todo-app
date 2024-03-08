<template>
    <li class="d-flex align-items-center list-group-item">
        <h4>{{ id }}</h4>
        <button
        v-if="!isEditing"
        :class="{completed}"
        @click="$emit('on-toggle')"
         class="btn border-0 text-left flex-grow-1">{{ todoText }}</button>
        <form v-else @submit.prevent="endEditing()" class="flex-grow-1">
            <input @blur="startEditing()" v-model="newtodoText" type="text" class="form-control" />
        </form>
        <button @click="startEditing()" class="btn btn-primary">Edit</button>
        <button @click="$emit('on-delete')" class="btn btn-danger">Delete</button>
    </li>
</template>

<script>
export default {
    props:{
        id: Number,
        todoText: String,
        completed: Boolean
    },
    data(){
        return {
            isEditing: false,
            newtodoText: ""
        } 
    },
    methods: {
        startEditing(){
            if(!this.isEditing){
                this.newtodoText = this.todoText;
                this.isEditing = true;
            }
            else{
                this.endEditing();
            }
        },
        endEditing(){
            this.isEditing = false;
            this.$emit('on-edit', this.newtodoText)
        }
    }
}
</script>

<style scoped>
.completed{
    text-decoration: line-through;
}
</style>