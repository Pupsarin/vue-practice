<template>
  <div>
    <label for="add-todo">Add todo </label>
    <input id="add-todo" v-bind:value="newToDo" v-on:input="updateValue($event.target.value)" name="add-todo" type="text"/>
  </div>

</template>

<script>
export default {
  name: 'CustomInput',
  props: ["newToDo"],
  methods: {
    updateValue(value) {
      this.$emit('input', value);
    }
  }
}
</script>