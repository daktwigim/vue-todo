<template>
  <div id="app">
    <todo-container></todo-container>
  </div>
</template>

<script>
import TodoContainer from "@/components/TodoContainer";

export default {
  name: "app",
  components: { TodoContainer }
};
</script>

<style lang="scss">
* {
  box-sizing: border-box;
}

body {
  background-color: #efefef;
}
</style>
