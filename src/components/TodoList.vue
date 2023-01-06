<script lang="ts" setup>
import { defineProps } from "vue";
import type { Todo } from "@/interfaces";

export interface Props {
  todos: Todo[];
  removeTodo: (id: string) => void;
}

const props = defineProps<Props>();
</script>

<template>
  <div class="todo-items" v-if="props.todos.length">
    <div class="todo-item" v-for="todo in props.todos" :key="todo.id">
      <label>{{ todo.text }} </label>
      <button v-on:click="removeTodo(todo.id)" class="delete-button">X</button>
    </div>
  </div>
</template>

<style scoped>
.todo-items {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  gap: 0.25rem;
  overflow-y: auto;
  width: 100%;
  border: 1px solid lightgray;
}
.todo-items::-webkit-scrollbar {
  width: 5px;
}
.todo-items::-webkit-scrollbar-track {
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
}

.todo-items::-webkit-scrollbar-thumb {
  background-color: darkgrey;
  border-radius: 10%;
}

.todo-item {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 0.5rem;
  border-bottom: 1px solid lightgray;
}

.delete-button {
  cursor: pointer;
  padding: 0.5rem;
  background-color: lightcoral;
  color: white;
}
</style>
