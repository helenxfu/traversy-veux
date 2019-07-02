<template>
  <div>
    <div class="container">
      <AddTodo />
      <FilterTodos />
      <Todos />
    </div>
  </div>
</template>

<script>
import Todos from "./components/Todos.vue";
import AddTodo from "./components/AddTodo";
import FilterTodos from "./components/FilterTodos";

export default {
  name: "app",
  components: {
    Todos,
    FilterTodos,
    AddTodo
  }
};
</script>

<style>
body {
  line-height: 1.6;
  background: rgb(245, 255, 243);
}
.container {
  max-width: 1100px;
  margin: auto;
  overflow: auto;
  padding: 0 5px;
}
</style>
