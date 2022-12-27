<script>
import TodoForm from "./components/TodoForm.vue";
import TodoList from "./components/TodoList.vue";

export default {
  components: {
    TodoForm,
    TodoList,
  },
  data: function () {
    return {
      todos: ["Work in this project", "Make a commit"],
    };
  },
};
</script>

<template>
  <h1>ToDoApp</h1>
  <TodoForm lb_name="New Task" input_name="new_task" />
  <h2>ToDoList</h2>
  <TodoList :todo="todos" />
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
  width: 85%;
  margin: 0 auto;
}
</style>
