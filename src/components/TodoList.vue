<template>
  <div class="box">
    <ul v-if="todos.length > 0" class="list">
      <todo-item v-for="item in todos" :key="item.id" v-bind:item.sync="item"></todo-item>
    </ul>
    <div v-else class="no-items">해야할 일이 없습니다 :)</div>
  </div>
</template>

<script>
import TodoItem from "@/components/TodoItem";

export default {
  name: "todo-list",
  components: { TodoItem },
  props: ["todos"],
  data() {
    return {
      newTodo: {
        title: "",
        done: false
      }
    };
  },
  methods: {
    createTodo: function() {
      this.$emit("createTodo", this.newTodo);
    }
  }
};
</script>

<style lang="scss" scoped>
.box {
  position: relative;
  background-color: #ffffff;
  padding: 0 8px;
  padding-bottom: 48px;

  border: 1px solid #dddddd;
  box-shadow: 4px 4px 8px rgba(44, 44, 44, 0.2);
}

.list {
  margin: 0;
  padding: 0;
}

.no-items {
  padding: 16px;
  text-align: center;
  color: #888888;
}
</style>