<template>
  <div class="add-todo">
    <form @submit="addTodo">
      <input type="text" placeholder="Add Tasks Here..." v-model="title" />
    </form>
  </div>
</template>

<script>
import { v4 } from 'uuid'
export default {
  name: 'addtodo',
  data() {
    return {
      title: ''
    }
  },
  methods: {
    addTodo(e) {
      e.preventDefault()
      if (this.title == '') return
      const newTodo = {
        id: v4(),
        title: this.title,
        completed: false
      }
      this.$emit('add-todo', newTodo)
      this.title = ''
    }
  }
}
</script>

<style scoped>
.add-todo {
  background: transparent;
  padding: 10px;
}

form {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

input {
  width: 50%;
  text-align: center;
  font-size: 20px;
  border: none;
  padding: 10px 10px;
  border-radius: 5px;
  box-shadow: 2px 3px 5px rgba(178, 184, 178, 0.411);
}
@media screen and (max-width: 800px) {
  input {
    width: 90%;
  }
}
</style>
