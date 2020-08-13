<template>
    <div class="todo">
        <todo-list list-name="My To-Do's" />
    </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";

export default {
    name: "App",
    components: {
        TodoList,
    },
};
</script>

<style>
body {
    margin: 0;
    padding: 0;
}
* {
    margin: 0;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
ul {
    list-style: none;
    padding: 0;
    margin: 0;
}
.todo {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    margin: auto;
}
</style>
