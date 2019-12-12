<template>
  <div class="creater">
    <input
      class="creater__input"
      type="text"
      placeholder="해야할 일을 적어주세요."
      v-model="newTodoTitle"
      @keyup.enter="createTodo"
    />
    <button class="creater__button" @click="createTodo">+</button>
  </div>
</template>

<script>
export default {
  name: "todo-creater",
  data() {
    return {
      newTodoTitle: "",
      isPuase: false,
      pauseDelay: 300
    };
  },
  methods: {
    createTodo: function(event) {
      if (!this.isPuase) {
        this.isPuase = true;
        this.$emit("createTodo", this.newTodoTitle);
        this.newTodoTitle = "";
        event.currentTarget.blur();

        setTimeout(() => {
          this.isPuase = false;
        }, this.pauseDelay);
      } else {
        return false;
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.creater {
  display: flex;

  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 50px;
  font-size: 0;

  border: 1px solid #dddddd;
}

.creater__input {
  flex: 1;

  height: 48px;
  padding: 8px;
  font-size: 16px;

  border: none;
  outline: none;
  vertical-align: top;
  color: #444444;

  &::placeholder {
    color: #dddddd;
  }
}

.creater__button {
  display: flex;
  vertical-align: center;
  justify-content: center;
  width: 60px;
  height: 48px;
  font-size: 24px;
  font-weight: 600;

  border: none;
  background-color: rgb(26, 206, 26);
  color: #ffffff;
  vertical-align: top;
}
</style>