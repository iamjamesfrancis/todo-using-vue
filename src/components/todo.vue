<template>
  <div class="todo">
    <div class="todo-list" v-bind:key="todo.id" v-for="todo in todos">
      <todos v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
    </div>
  </div>
</template>

<script>
import Todos from './todos.vue'
export default {
  components: { Todos },
  name: 'Todo',
  props: ['todos']
}
</script>

<style scoped>
.todo {
  /* background: rgb(255, 255, 255); */
  background: transparent;
  width: 50%;
  margin: auto;
  height: 70%;
  overflow-y: scroll;
}
@media screen and (max-width: 800px) {
  .todo {
    width: 90%;
  }
}
</style>
