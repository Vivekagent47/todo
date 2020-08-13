<template>
    <div class="container">
        <div class="row">
            <div class="heading">
                <h1>{{ listName }}</h1>
            </div>
        </div>
        <div>
            <create-todo @on-new-todo="addTodo($event)" />
        </div>
        <div class="row">
            <div class="list">
                <ul class="list-group">
                    <todo
                        v-for="(todo, index) in todos"
                        :key="index"
                        :description="todo.description"
                        :completed="todo.completed"
                        @on-toggle="toggleTodo(todo)"
                        @on-delete="deleteTodo(todo)"
                        @on-edit="editTodo(todo, $event)"
                    />
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
import Todo from "./Todo.vue";
import CreateTodo from "./CreateTodo.vue";

export default {
    props: {
        listName: String,
    },
    data() {
        return {
            todos: [
                { description: "Hello", completed: false },
                { description: "Do this", completed: false },
            ],
        };
    },
    methods: {
        addTodo(newTodo) {
            this.todos.push({ description: newTodo, completed: false });
        },
        toggleTodo(todo) {
            todo.completed = !todo.completed;
        },
        deleteTodo(deletedTodo) {
            this.todos = this.todos.filter(todo => todo !== deletedTodo);
        },
        editTodo(todo, newTodoDescription) {
            todo.description = newTodoDescription;
        },
    },
    components: { 
        Todo, CreateTodo 
    },
};
</script>

<style scoped>
.heading {
    font-size: 24px;
    text-align: center;
    color: #222222;
}
.row {
    margin: 50px 0;
    padding: 0;
}
</style>
