<template>
  <div class='todo-item'>
    <p v-bind:class="{'is-complete': todo.completed}">
      <input type="checkbox" v-on:change="markComplete">
      {{todo.title}}
    </p>
    <button @click="$emit('del-todo', todo.id)" class="del_button">Delete</button>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: ['todo'],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    },
  },
};
</script>

<style lang="scss" scoped>

  .todo-item{
    height: 3rem;
    display: flex;
    align-items: center;
    padding: 0 1rem;
    border-bottom: 1px solid #eeeeee;
    p{
      display: flex;
      align-items: center;
    }
  };

  input[type="checkbox"]{
    width: 1rem;
    height: 1rem;
    margin-right: 1rem;
  }
  // input[type="checkbox"]{
  //   -webkit-appearance: none;
  //   border: 1px solid #d1d1d1;
  //   width: 20px;
  //   height: 20px;
  //   border-radius: 2px;
  //   margin-right: 1rem;
  //   &:checked{
  //     background-color: rgb(85, 85, 250);
  //   }
  // }

  .is-complete{
    text-decoration: line-through;
  };

  .del_button{
    background: none;
    border: none;
    color: red;
    margin-left: auto;
  }

</style>
