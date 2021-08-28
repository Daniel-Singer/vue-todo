<template>
  <div id='app'>
    <Header />
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>

import Todos from './components/Todos.vue';
import Header from './components/layout/Header.vue';
import AddTodo from './components/AddTodo.vue';

export default {
  name: 'App',
  components: {
    Todos,
    Header,
    AddTodo,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    },
  },
};
</script>

<style lang="scss">

@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@100;300;400;700&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
};

body{
  font-family: 'Montserrat', sans-serif;
  height: 100vh;
  width: 100vw;
  display: flex;
  align-items: center;
  justify-content: center;
};

#app{
  width: 50%;
  height: 300px;
  box-shadow: 0px 3px 5px rgba(0,0,0,.2);
}
</style>
