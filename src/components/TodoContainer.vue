<script lang="ts" setup>
import { ref } from "vue";
import { v4 as uuidv4 } from "uuid";
import type { Todo } from "@/interfaces";
import TodoInputVue from "./TodoInput.vue";
import TodoListVue from "./TodoList.vue";

const todos = ref<Todo[]>([]);

function addTodo(e: any): void {
  todos.value.push({
    id: uuidv4(),
    text: e.target.value,
  });
}

function removeTodo(id: string) {
  todos.value = todos.value.filter((val) => val.id != id);
}
</script>

<template>
  <div class="menu">
    <h1>Todo List App</h1>
    <h2>Press enter to add todo element</h2>
    <TodoInputVue :add-todo="addTodo" /><TodoListVue
      :todos="todos"
      :removeTodo="removeTodo"
    />
  </div>
</template>

<style scoped>
.menu {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  height: 50vh;
}
</style>
