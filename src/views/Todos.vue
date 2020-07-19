<template>
  <div>
    <h2>List </h2>
    <router-link to="/" >Back to home</router-link>
    <AddTodo
      @add-todo="addTodo"
    />
    <hr>
    <Loader v-if="loading" />
    <ul v-if="!loading" >
      <TodoItem
        v-for="(todo, i) of todos"
        v-bind:todo="todo"
        v-bind:index="i"
        v-bind:key="i"
        @remove-todo="removeTodo"
      />
    </ul>
    <span v-if="!loading && !todos.length">List is empty!</span>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem.vue';
import Loader from '@/components/Loader.vue';
import AddTodo from '@/components/AddTodo.vue';

export default {
  components: { TodoItem, Loader, AddTodo },
  created() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=13')
      .then((response) => response.json())
      .then((json) => { this.todos = json; this.loading = false; });
  },
  data() {
    return {
      todos: [],
      loading: true,
    };
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    addTodo(todo) {
      this.todos.push(todo);
    },
  },
};
</script>

<style scoped>
  ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }
</style>
