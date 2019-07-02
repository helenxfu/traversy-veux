<template>
  <div>
    <h1>Traversy Todos</h1>
    <div class="todos">
      <div
        v-for="todo in allTodos"
        :key="todo.id"
        class="todo"
        @dblclick="onDblClick(todo)"
        :class="{'is-complete':todo.completed}"
      >
        {{todo.title}}
        <span class="delete" @click="deleteTodo(todo.id)">x</span>
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions, mapGetters } from "vuex";

export default {
  name: "Todos",
  methods: {
    ...mapActions(["fetchTodos", "deleteTodo", "updateTodo"]),
    onDblClick(todo) {
      const updTodo = {
        id: todo.id,
        title: todo.title,
        completed: !todo.completed
      };
      this.updateTodo(updTodo);
    }
  },
  computed: mapGetters(["allTodos"]),
  created() {
    this.fetchTodos();
  }
};
</script>

<style scoped>
h1 {
  text-align: center;
  font-size: 30px;
}
.todos {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 10px;
  text-align: center;
}

.todo {
  border: 1.2px dashed rgb(16, 77, 31);
  background: rgb(211, 248, 155);
  padding: 10px;
  border-radius: 5px;
  cursor: pointer;
  position: relative;
}
.is-complete {
  border-color: rgb(244, 255, 97);
  background: rgb(0, 61, 46);
  color: rgb(255, 255, 230);
}
.delete {
  position: absolute;
  bottom: 0;
  right: 0;
  color: rgb(173, 0, 0);
}
</style>