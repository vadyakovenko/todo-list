<template>
  <form
    @submit.prevent="onSumbmit"
  >
    <input type="text" v-model="title">
    <button type="submit">+ Create</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: '',
    };
  },
  methods: {
    onSumbmit() {
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false,
        };

        this.$emit('add-todo', newTodo);
        this.title = '';
      }
    },
  },
};
</script>

<style scoped>
  form {
    display: flex;
    margin-bottom: 10px;
  }
  input {
    width: 400px;
  }
  button {
    background: #00c486;
    border: 1px solid #31455f;
    border-radius: 4px;
    color: #31455f;
  }
</style>
