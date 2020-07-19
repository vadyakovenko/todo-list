<template>
  <li>
    <span v-bind:class="{done: todo.completed}">
      <input v-model="todo.completed" type="checkbox" @click="todo.completed = !todo.completed">
      <strong>{{index+1}}</strong>
      {{todo.title}}
    </span>
    <button class="rm" @click="$emit('remove-todo', todo.id)">&times;</button>
  </li>
</template>

<script>
export default {
  name: 'TodoItem',
  props: {
    todo: {
      type: Object,
      required: true,
    },
    index: Number,
  },
};
</script>

<style scoped>
  li  {
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    padding: .5rem 2rem;
    margin-bottom: 1rem;
  }

  input {
    margin-right: 1rem;
  }

  .rm {
    background: red;
    color: azure;
    font-weight: bold;
    border: none;
  }
  .done {
    text-decoration: line-through;
  }
</style>
