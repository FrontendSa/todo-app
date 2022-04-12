<template>
  <div class="todo-list">
    <todo-item
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @changeState="todo.completed = $event.target.checked"
    ></todo-item>
  </div>
</template>

<script>
import TodoItem from "./TodoItem";

export default {
  name: "TodoList",
  components: { TodoItem },
  props: ["todos"],
};
</script>

<style>
.todo-list {
  display: grid;
  row-gap: 14px;
}
</style>
