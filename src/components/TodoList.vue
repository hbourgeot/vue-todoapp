<script>
export default {
  props: ["todo"],
};
</script>

<template>
  <ul>
    <li v-for="task in todo" :key="task" class="item">
      {{ task }} <button>Remove</button>
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
  widows: 100%;
  margin: 0 0 12px;
  padding: 12px 24px;

  button {
    background-color: #a0a4d9;
    border-radius: 6px;
    color: #000;
    border: 1px solid #a0a4d9;
    font-family: Arial, Helvetica, sans-serif;
    font-weight: 700;
    padding: 6px;
    text-align: center;
  }
}

ul {
  padding: 10px;
}
</style>
