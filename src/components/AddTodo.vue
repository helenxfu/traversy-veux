<template>
  <div>
    <h2>Add Todo</h2>
    <div class="add">
      <form @submit="onSubmit">
        <input type="text" v-model="title" placeholder="Add Todo..." />
        <input type="submit" value="submit" />
      </form>
    </div>
  </div>
</template>

<script>
import { mapActions } from "vuex";

export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    ...mapActions(["addTodo"]),
    onSubmit(e) {
      e.preventDefault();
      this.addTodo(this.title);
      this.title = "";
    }
  }
};
</script>

<style scoped>
form {
  display: flex;
}
input[type="text"] {
  flex: 10;
  border: 1px solid green;
  outline: none;
}
input[type="submit"] {
  flex: 2;
  background: green;
  border: 1px solid rgb(118, 211, 75);
  color: white;
  cursor: pointer;
  outline: none;
  padding: 4px;
}
</style>