<template>
  <div class="input-wrapper">
    <input
      autofocus
      class="add-task"
      placeholder="Add a new task"
      v-model="text"
      @keyup.enter="handleOnPressEnter"
    />
  </div>
</template>

<script lang="ts" setup>
import { ref, defineProps, withDefaults } from "vue";
export interface Props {
  addTodo: (e: any) => void;
}
const text = ref("");

const props = withDefaults(defineProps<Props>(), {
  addTodo: () => {},
});

function handleOnPressEnter(e: any) {
  text.value = "";
  props.addTodo(e);
}
</script>

<style scoped>
.input-wrapper {
  width: 100%;
}

input {
  width: 100%;
  padding: 0.5rem;
}
</style>
