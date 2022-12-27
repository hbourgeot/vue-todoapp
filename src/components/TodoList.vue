<script>
export default {
  props: {
    todo: Object,
    removeTodo: Function,
    doneTodo: Function,
  },
  created() {
    console.log(this.$props.todo);
  },
};
// TODO: Make a event of remove
</script>

<template>
  <ul>
    <li v-for="(task, index) in todo" :key="index" class="item">
      <span :class="{ task_done: task.done }">{{ task.content }}</span>
      <div class="btns">
        <button @click="doneTodo(task)" class="done">
          <span v-if="!task.done">Done</span>
          <span v-else>Undone</span>
        </button>
        <button @click="removeTodo(index)" class="remove">Remove</button>
      </div>
    </li>
  </ul>
</template>

<style lang="scss">
.item {
  display: flex;
  align-items: center;
  border-radius: 6px;
  border: 2px solid darken(#fff, 50%);
  list-style-type: none;
  justify-content: space-between;
  margin: 0 0 12px;
  padding: 12px 24px;
  @media (max-width: 768px) {
    flex-direction: column;
    align-items: flex-start;
  }

  button {
    border-radius: 6px;
    color: #000;
    font-family: Arial, Helvetica, sans-serif;
    font-weight: 700;
    padding: 6px;
    text-align: center;
    @media (max-width: 768px) {
      width: 100%;
    }
  }
}

.task_done {
  text-decoration: line-through;
}

.btns {
  width: fit-content;
  display: flex;
  justify-content: space-between;
  gap: 5px;
  @media (max-width: 768px) {
    width: 100%;
    margin-top: 10px;
  }
}

.done {
  background-color: #080;
  &:hover,
  &.checked {
    background-color: lighten(#080, 20%);
  }
}

.remove {
  background-color: #800;
  &:hover {
    background-color: lighten(#800, 20%);
  }
}

ul {
  padding: 10px;
}
</style>
