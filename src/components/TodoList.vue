<template>
        <div class="container">
            <div class="row">
                <div class="col-12">
                    <p class="display-3">MY Todo</p>
                </div>
            </div>
            <div class="row">
                <AddTodo @on-addtodo="addTodo($event)"/>
            </div>
            <div class="row">
                <div class="col-12 col-lg-6">
                    <ul class="list-group">
                        <TodoItem v-for="(todo,index) in todos"
                        :id="todo.id"
                        :key="index"
                        :todoText= "todo.todoText"
                        :completed= "todo.completed"
                        @on-delete="deleteTodo(todo.todoText)"
                        @on-edit="editTodo(todo, $event)"
                        @on-toggle="toggleTodo(todo)"
                        />
                    </ul>
                </div>
            </div>
        </div>
</template>

<script>
import TodoItem from './TodoItem.vue';
import AddTodo from './AddTodo.vue';
export default {
    components:{
        TodoItem,
        AddTodo
    },
    data(){
        return {
            todos:[
                {"id":1, todoText: "Do 2 DSA question", completed: false},
                {"id":2, todoText: "complete assignment", completed: false},
                {"id":3, todoText: "read 10 questions from react github repo", completed: false},
                {"id":4, todoText: "Do exercise atleast 1 hour", completed: false},
                {"id":5, todoText: "complete signup functionality", completed: false}
            ]
        }
    },
    methods:{
        addTodo(newTodo,nextid){
            this.todos.push({
                todoText: newTodo,
                completed: false,
                id: nextid
            });
        },
        editTodo(todo,newtodoText){
            todo.todoText = newtodoText;
        },
        deleteTodo(deleteTodo){
            this.todos = this.todos.filter(
                todo => todo.todoText != deleteTodo
            )
        },
        toggleTodo(todo){
            todo.completed = !todo.completed;
        }   
    }
}
</script>

<style>

</style>