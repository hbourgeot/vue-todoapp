<script>
import TodoForm from "./components/TodoForm.vue";
import TodoList from "./components/TodoList.vue";
import { ref } from "vue";
export default {
  components: {
    TodoForm,
    TodoList,
  },
  setup() {
    const defaultTodo = [{ done: false, content: "Create this project" }];
    const todoData = JSON.parse(localStorage.getItem("todos")) || defaultTodo;
    const todos = ref(todoData);

    function addItem(newTask) {
      if (newTask) {
        todos.value.push({ done: false, content: newTask });
      }

      newTask = "";
      saveData();
    }
    function saveData() {
      localStorage.setItem("todos", JSON.stringify(todos.value));
    }

    function removeTodo(index) {
      todos.value.splice(index, 1);
      saveData();
    }

    function doneTodo(todo) {
      todo.done = !todo.done;
      saveData();
    }

    return {
      todos,
      addItem,
      saveData,
      removeTodo,
      doneTodo,
    };
  },
};
</script>

<template>
  <h1>ToDoApp</h1>
  <TodoForm
    lb_name="New Task"
    input_name="newTask"
    :addItem="addItem"
    :saveData="saveData"
  />
  <h2>ToDoList</h2>
  <TodoList :todo="todos" :removeTodo="removeTodo" :doneTodo="doneTodo" />
</template>

<style lang="scss">
body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  background-color: #27292d;
  color: white;
  box-sizing: border-box;

  h1 {
    text-align: center;
  }

  h2 {
    border-bottom: 1px solid #bbb;
    font-weight: 700;
    margin: 18.26px 0;
    padding: 0 0 6px;
  }
}

#app {
  width: min(600px, 85%);
  margin: 0 auto;
}
</style>
