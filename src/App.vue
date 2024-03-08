<template>
  <div>
    <h1>Welcome to my vue todo app</h1>
    <TodoList/>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue';
export default {
  name: 'App',
  components: {
    TodoList
  }
}
</script>

<style>
  body{
    background-color: rgb(66,66, 66);
    color: white;
  }
</style>