<template>
    <form class="form" @submit.prevent="addTodo()">
        <input
            v-model="newTodo"
            type="text"
            class="form-control"
            placeholder="Create a new to-do..."
        />
    </form>
</template>

<script>
export default {
    data() {
        return {
            newTodo: ""
        };
    },
    methods: {
        addTodo() {
            if (this.newTodo.length > 0) {
                this.$emit("on-new-todo", this.newTodo);
            }
            this.newTodo = "";
        }
    }
};
</script>

<style scoped>
.form input{
    padding: 10px;
    width: 400px;
    border: 2px solid #9b9b9b;
    border-radius: 4px;
}
</style>
