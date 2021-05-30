<template>
  <div class="main-container">
    <div class="list-container">
      <h1>BADIN KITCHEN</h1>
      <TodoList />
    </div>
  </div>
</template>

<script>
import TodoList from "./components/todoList.vue";

export default {
  name: "App",
  components: {
    TodoList,
  },
};
</script>

<style>
body {
  margin: 0;
}
.main-container {
  widows: 100vw;
  height: 100vh;
  background: rgb(2, 0, 36);
  background: linear-gradient(
    90deg,
    rgba(2, 0, 36, 1) 0%,
    rgba(9, 9, 121, 1) 35%,
    rgba(0, 212, 255, 1) 100%
  );
}
.list-container {
  padding-top: 10vh;
  display: flex;
  align-items: center;
  flex-direction: column;
}
</style>
