<template>
  <div>
      <TodoItem
        v-for="todo in todos"
        v-bind:key="todo.id"
        v-bind:todo="todo"
        v-on:del-todo="$emit('del-todo', todo.id)"
      />
  </div>
</template>

<script>

import TodoItem from './TodoItem.vue';

export default {
  name: 'Todos',
  components: {
    TodoItem,
  },
  props: ['todos'],
};
</script>

<style lang="scss" scoped>

</style>
