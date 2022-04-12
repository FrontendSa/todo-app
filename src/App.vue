<template>
  <main>
    <div class="container">
      <h1>欢迎使用待办事项</h1>
      <todo-add :tid="todos.length" @addTodo="addTodo"></todo-add>
      <todo-filter
        :selected="filter"
        @changeFilter="filter = $event"
      ></todo-filter>
      <todo-list :todos="filteredTodos"></todo-list>
    </div>
  </main>
</template>

<script>
import TodoAdd from "./components/TodoAdd";
import TodoFilter from "./components/TodoFilter";
import TodoList from "./components/TodoList";
import useTodos from "@/composables/useTodos";
import useFilteredTodos from "@/composables/useFilteredTodos";

export default {
  name: "App",
  components: { TodoAdd, TodoFilter, TodoList },
  setup() {
    const { todos, addTodo } = useTodos();
    const { filter, filteredTodos } = useFilteredTodos(todos);

    return {
      todos,
      addTodo,
      filter,
      filteredTodos,
    };
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: Helvetica, "PingFang SC", "Microsoft Yahei", sans-serif;
}

/* 整个页面 */
main {
  width: 100vw;
  min-height: 100vh;
  display: grid;
  align-items: center;
  justify-items: center;
  background: rgb(203, 210, 240);
  padding: 50px 0;
}

.container {
  width: 60%;
  max-width: 400px;
  box-shadow: 0 0 24px rgba(0, 0, 0, 0.15);
  border-radius: 24px;
  padding: 48px 28px;
  background-color: rgb(245, 246, 252);
}

/* 标题 */
h1 {
  margin: 24px 0;
  font-size: 28px;
  color: #414873;
  text-align: center;
}
</style>
