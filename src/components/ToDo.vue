<template>
  <div>
    <div>TODO</div>
    <ol>
      <li v-for="(todo, index) in localTodos" :key="todo.text + index">
        <input type="checkbox" :checked="todo.done" @click="toggleToDo(index, todo)" />
        {{ todo.text }}
        <button @click="removeTodo(index)">remove</button>
      </li>
    </ol>
  </div>
</template>


<script>

export default {
  name: 'ToDo',
  props: ["todos"],
  data() {
    return {
      localTodos: []
    }
  },
  created() {
    this.localTodos = this.todos;
  },
  methods: {
    toggleToDo(index, todo) {
      this.localTodos[index].done = !todo.done;
      this.$emit('toggle-todo', this.localTodos);
    },
    removeTodo(index) {
      this.localTodos.splice(index, 1);
      this.$emit('remove-todo', this.localTodos);
    }
  }
}
</script>