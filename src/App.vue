<template>
  <div id="app">
    <img src="./assets/logo.png">
    <AddTodoItem @newTodo="addItem"></AddTodoItem>
    <TodoItem v-for="(todo, index) in uncompletedTodos" :key="`todo-${index}`" :item="todo" />
    <h3>Completed</h3>
    <div class="completed-item" v-for="(completedTodo, index) in completedTodos" :key="`completed-todo-${index}`">
      {{ completedTodo.label }}
    </div>
  </div>
</template>

<script>
import AddTodoItem from './components/AddTodoItem.vue';
import TodoItem from './components/TodoItem.vue';

export default {
  computed: {
    completedTodos() {
      return this.todos.filter(todo => todo.isChecked);
    },
    uncompletedTodos() {
      return this.todos.filter(todo => !todo.isChecked);
    }
  },
  data: () => ({
    todos: [
      {
        label: 'Write Angular ToDo example',
        isChecked: false
      },
      {
        label: 'Write React ToDo example',
        isChecked: false
      },
      {
        label: 'Write Vue ToDo example',
        isChecked: true
      }
    ]
  }),
  name: 'app',
  components: {
    AddTodoItem,
    TodoItem
  },
  methods: {
    addItem(item) {
      this.todos.unshift({
        label: item,
        isChecked: false
      });
    }
  }
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.completed-item {
  text-decoration: line-through;
}
</style>
