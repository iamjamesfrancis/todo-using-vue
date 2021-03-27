<template>
  <div id="app">
    <link
      rel="stylesheet"
      href="https://fonts.googleapis.com/icon?family=Material+Icons"
    />
    <Header />
    <addtodo v-on:add-todo="addTodo" />
    <todo v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Addtodo from './components/addtodo.vue'
import Header from './components/header.vue'
import Todo from './components/todo.vue'
export default {
  name: 'App',
  components: { Todo, Header, Addtodo },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: 'Task 1',
          completed: true
        },
        {
          id: 2,
          title: 'Task 2',
          completed: false
        },
        {
          id: 3,
          title: 'Task 3',
          completed: false
        }
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo]
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');
* {
  margin: 0;
  padding: 0;
  font-family: 'Poppins', sans-serif;
  user-select: none;
  outline: none;
}
#app {
  background: linear-gradient(
    45deg,
    rgb(89, 248, 182),
    rgb(59, 253, 172),
    rgb(4, 255, 150)
  );
  width: 100%;
  height: 100vh;
  margin: auto;
  overflow: hidden;
}

::-webkit-scrollbar {
  width: 5px;
}
::-webkit-scrollbar-thumb {
  border-radius: 5px;
  background: rgba(134, 138, 137, 0.726);
}
@media screen and (max-width: 800px) {
  #app {
  }
}
</style>
