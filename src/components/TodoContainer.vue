<template>
  <div class="container">
    <h1 class="title">Vue Todo List</h1>
    <todo-list :todos="todos"></todo-list>
    <todo-creater @createTodo="createTodo"></todo-creater>
  </div>
</template>

<script>
import TodoList from "@/components/TodoList";
import TodoCreater from "@/components/TodoCreater";

export default {
  name: "todo-container",
  components: { TodoList, TodoCreater },
  data() {
    return {
      todos: [],
      idCounter: 0
    };
  },
  methods: {
    createTodo: function(newTodoTitle) {
      this.todos.push({
        id: this.idCounter,
        title: newTodoTitle,
        done: false
      });

      this.idCounter++;
    }
  }
};
</script>

<style lang="scss" scoped>
.container {
  position: relative;
  margin: 0 auto;
  margin-top: 80px;
  width: 500px;
}

.title {
  color: #444444;
  text-align: center;
}
</style>