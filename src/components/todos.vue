<template>
  <div class="todos" v-bind:class="{ 'is-completed': todo.completed }">
    <input type="checkbox" v-on:change="markComplete" v-if="!todo.completed" />
    <input type="checkbox" v-on:change="markComplete" v-else checked />
    <div class="todo-item" v-on:click="markComplete">{{ todo.title }}</div>
    <div class="cancel-btn" v-on:click="$emit('del-todo', todo.id)">
      <span class="material-icons">
        delete
      </span>
    </div>
  </div>
</template>

<script>
// import jquery from 'jquery'
export default {
  name: 'todos',
  props: ['todo'],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed
    }
  }
}
</script>

<style scoped>
.is-completed {
  text-decoration: line-through;
}
.todos {
  display: flex;
  align-items: flex-start;
  padding: 1rem;
  margin-top: 1rem;
  justify-content: space-evenly;
  background: rgb(255, 255, 255);
  border-radius: 5px;
  margin-right: 10px;
  box-shadow: 2px 3px 5px rgba(178, 184, 178, 0.411);
}
.todo-item {
  flex: 1;
  margin-left: 2rem;
}
input[type='checkbox'] {
  cursor: pointer;
  min-width: 20px;
  min-height: 20px;
}
.cancel-btn span {
  color: red;
}
@media screen and (max-width: 800px) {
}
</style>
