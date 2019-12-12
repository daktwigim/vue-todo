<template>
  <li class="item" :class="{'item__active': item.done}">
    <input class="item__input" :id="item.id" type="checkbox" v-model="item.done" />
    <label class="item__label" :for="item.id"></label>
    <span class="item__title">{{ item.title }}</span>
    <button class="item__button">✕</button>
  </li>
</template>

<script>
export default {
  name: "todo-item",
  props: ["item"],
  data() {
    return {};
  }
};
</script>

<style lang="scss" scoped>
.item {
  display: flex;
  align-items: center;

  width: 100%;
  height: 48px;
  padding: 0;

  list-style: none;

  &:hover .item__button {
    display: block;
  }
}

.item__input {
  display: none;
}

.item__input + .item__label {
  margin-right: 8px;
  width: 32px;
  height: 32px;
  border-radius: 100%;
  border: 1px solid #dddddd;
  cursor: pointer;
}

.item__title {
  flex: 1;
  font-size: 18px;
  color: #444444;
}

.item__button {
  display: none;
  justify-content: flex-end;
  width: 32px;
  height: 32px;

  border: none;
  outline: none;

  font-size: 24px;
  color: rgb(204, 48, 48);
  cursor: pointer;
}

.item__active {
  .item__label {
    position: relative;
    border-color: rgb(26, 206, 26);

    &:after {
      position: absolute;
      left: 50%;

      display: inline-block;
      content: "";
      width: 14px;
      height: 10px;
      border: 3px solid rgb(26, 206, 26);
      border-top: 0;
      border-right: 0;
      transform: rotate(-45deg) translate(-61%, -9%);
    }
  }

  .item__title {
    color: #dddddd;
    text-decoration: line-through;
  }
}
</style>