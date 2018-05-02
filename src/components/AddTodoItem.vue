<template>
  <form v-on:submit.prevent="onSubmit">
    <input
      placeholder="Enter new todo item"
      name="formValue"
      type="text"
      v-model="itemValue"
    />
  </form>
</template>

<script>
export default {
  data: () => {
    return {
      itemValue: ''
    };
  },
  name: 'AddTodoItem',
  methods: {
    onSubmit() {
      this.$emit('newTodo', this.itemValue);
      this.itemValue = '';
    }
  }
};
</script>

<style scoped>
input {
  font-size: 1rem;
  margin: 1em 0;
}
</style>
