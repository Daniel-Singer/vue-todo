<template>
  <div>
    <form @submit="addTodo">
      <input type="text" v-model="title" placeholder="Add Todo...">
      <input type="submit" value="Submit" class="btn">
    </form>
  </div>
</template>

<script>

import { v4 as uuidv4 } from 'uuid';

export default {
  name: 'AddTodo',
  data() {
    return {
      title: '',
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const newTodo = {
        id: uuidv4(),
        title: this.title,
        completed: false,
      };
      this.$emit('add-todo', newTodo);
      this.title = '';
    },
  },
};
</script>

<style lang="scss">
  form{
    display: flex;
    input[type="text"]{
      width: 100%;
      height: 2.5rem;
      padding: 0 1rem;
      font-size: 1rem;
      border: none;
      background-color: rgb(2, 2, 10);
      color: rgba(255,255,255, .8);
      &::placeholder{
        color: rgba(255, 255, 255, 0.8);
      };
      &:focus{
        outline: none;
      }
    }
    .btn{
      width: 25%;
      text-transform: uppercase;
      border: none;
      background-color: rgb(219, 0, 219);
      color: #fff;
    }
  }
</style>
