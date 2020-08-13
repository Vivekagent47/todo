<template>
     <li>
     <button
          :class="{ completed }"
          @click="$emit('on-toggle')"
          v-if="!isEditing"
     >
          <span>{{ description }}</span>
     </button>
     <form v-else class="edit-form" @submit.prevent="finishEditing()">
          <input
          type="text"
          class="form-control"
          v-model="newTodoDescription"
          @blur="finishEditing()"
          ref="newTodo"
          />
     </form>
     <button
          @click="startEditing()"
          class="edit"
     >
          <img src="../assets/edit.svg">
     </button>
     <button 
          @click="$emit('on-delete')" 
          class="del"
     >
          <img src="../assets/trash.svg">
     </button>
     </li>
</template>

<script>
export default {
     data() {
          return {
               isEditing: false,
               newTodoDescription: ""
          };
     },
     props: {
          description: String,
          completed: Boolean
     },
     methods: {
          startEditing() {
               if (this.isEditing) {
                    this.finishEditing();
               } 
               else {
                    this.newTodoDescription = this.description;
                    this.isEditing = true;
                    this.$nextTick(() => this.$refs.newTodo.focus());
               }
          },
          finishEditing() {
               this.isEditing = false;
               this.$emit("on-edit", this.newTodoDescription);
          }
     }
};
</script>

<style>
.completed {
     text-decoration: line-through;
     border: none;
}
li {
     border-collapse: collapse;
}
li button {
    background: none;
    border: none;
    border-collapse: collapse;
    padding: 20px;
    font-size: 20px;
}
li button img {
     width: 20px;
}
li button:nth-child(1){
     width: 300px;
     text-align: start;
}
.edit-form input{
     width: 300px;
     text-align: start;
     background: none;
     border: none;
     border-collapse: collapse;
     padding: 20px;
}
.edit-form {
     border: none;
}
</style>
