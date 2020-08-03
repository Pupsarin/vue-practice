<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    {{counter}}
      <CustomInput @input="inputHandler" v-bind:new-to-do="newToDo"/>
      <button :disabled="!Boolean(newToDo)" @click="addToDo()">add todo</button>
    <ToDo v-bind:todos="todos" v-on:remove-todo="updater" v-on:toggle-todo="updater"/>
  </div>
</template>

<script>
import ToDo from './components/ToDo.vue';
import CustomInput from "./components/CustomInput";


export default {
  name: 'App',
  data() {
    return {
      newToDo: '',
      todos: [],
      counter: 0
    }
  },
  methods: {
    updater() {
      // vse slomalo //todo: read the docs vm.$set
      // this.$set(this.todos, 0, todos);
    },
    inputHandler(variable) {
      this.newToDo = variable
    },
    addToDo() {
      if (this.newToDo) {
        this.todos.push({text: this.newToDo, done: false});
        this.newToDo = '';
      }
    },
  },
  watch: {
    todos() {
      this.counter = this.todos.reduce((acc, todo) => {
        if (todo.done) {
          return acc
        }
        return acc += 1;
      }, 0)
    }
  },
  components: {
    ToDo,
    CustomInput
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
