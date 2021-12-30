<template>
  <di>
    <h1>Todos</h1>
    <ul>
      <li v-for="todo of todos" :key="todo.id">
        {{ todo.name }}
      </li>
    </ul>
  </di>
</template>

<script>
import axios from "axios";

export default {
  name: "TodoList",
  data() {
    return {
      todos: []
    };
  },
  async created() {
    try {
      const res = await axios.get(`http://localhost:3000/todos`);

      this.todos = res.data;
    } catch (e) {
      console.error(e);
    }
  }
};
</script>

<style scoped>
h1 {
  color: aqua;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  color: #f0f;
}
</style>