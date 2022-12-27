<template>
  <form action="post" class="input-field" @submit.prevent="resetAndAdd">
    <label :for="input_name">{{ lb_name }}</label>
    <input type="text" :name="input_name" :id="input_name" v-model="newTask" />
    <button type="submit" class="btn-primary">Add Task</button>
  </form>
</template>

<script>
export default {
  props: {
    lb_name: String,
    input_name: String,
    saveData: Function,
    addItem: Function,
  },
  methods: {
    resetAndAdd: function () {
      this.addItem(this.newTask);
      document.querySelector(`#${this.input_name}`).value = "";
    },
  },
};
// TODO: Make a click event to push to array the tasks
</script>

<style lang="scss">
label {
  font-size: 14px;
  font-weight: 700;
}

input {
  border: 2px solid darken(#fff, 50%);
  border-radius: 6px;
  background-color: inherit;
  font-family: Arial;
  font-size: 18px;
  margin: 6px 0px 12px;
  padding: 12px 1px;
  outline: 0;
  color: white;
}

.btn-primary {
  background-color: #a0a4d9;
  border: 1px solid #a0a4d9;
  border-radius: 5px;
  color: #1f2023;
  font-family: Arial, Helvetica, sans-serif;
  font-size: 18px;
  font-weight: 700;
  margin: 6px 0px 12px;
  padding: 12px 1px;
  text-align: center;
}

.input-field {
  display: flex;
  flex-direction: column;
}
</style>
