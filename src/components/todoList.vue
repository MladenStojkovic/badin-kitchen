<template>
  <div class="input-container">
    <input class="input" v-model="newTodo" @keyup.enter="addTodo" />
    <div class="add" @click="addTodo">Add todo</div>
    <div v-if="todoList">
      <div class="todoList" v-for="todo in todoList" :key="todo.id">
        <div class="todo">{{ todo.name }}</div>
        <div class="del" @click="deleteTodo(todo.id)">delete</div>
      </div>
    </div>
    <div v-else>nema</div>
  </div>
</template>

<script>
import { db } from "../../firebase/dataBase";
export default {
  name: "TodoList",
  data() {
    return {
      todoList: [],
      newTodo: "",
    };
  },
  methods: {
    async addTodo() {
      if (this.newTodo) {
        console.log(this.todoList);

        await db.collection("todoList").add({
          name: this.newTodo,
        });
        this.newTodo = "";
      }
    },
    deleteTodo(id) {
      db.collection("todoList")
        .doc(id)
        .delete();
    },
  },
  // async mounted() {
  //   this.todoList = await db.collection("todoList");
  // },
  firestore: { todoList: db.collection("todoList") },
};
</script>

<style scoped>
/* .input-container {
  display: flex;
  width: 10vw;
  align-items: center;
  justify-content: space-between;
  background-color: aqua;
} */
.add {
  background-color: brown;
  margin-top: 10px;
  border-radius: 15px;
}
.add:hover {
  cursor: pointer;
}
.del:hover {
  cursor: pointer;
}
.todo {
  background-color: black;
}

.todoList {
  margin: 10px 0;
}
.del {
  background-color: crimson;
}
.input {
  width: 15vw;
  height: 3vh;
}
</style>
