<template>
  <div>
    <h1>List todos</h1>
    <hr />
    <div>
      <ul>
        <li v-for="todo in todos">
          <router-link
            :to="{
              name: 'DetailTodo',
              params: { id: todo.id },
            }"
          >
            {{ todo.title }}
          </router-link>
        </li>
      </ul>
    </div>
    <hr />
    <router-view />
  </div>
</template>

<script>
export default {
  name: "Todos",

  data() {
    return {
      todos: [],
    };
  },
  created() {
    fetch("https://jsonplaceholder.typicode.com/todos?userId=1")
      .then((response) => response.json())
      .then((dataTodos) => {
        this.todos = dataTodos;
      })
      .catch(console.log);
  },
};
</script>

<style lang="css" scoped></style>
