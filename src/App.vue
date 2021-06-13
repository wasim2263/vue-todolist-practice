<template>
  <div id="app">
    <to-do-form @todo-added="addToDo"></to-do-form>
    <h1>To-Do List</h1>
    <ul>
      <li v-for="item in TodoLists" :key="item.id">
        <todo-list :label="item.label" :done="item.done" :id="item.id"></todo-list>
      </li>
    </ul>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue';
import uniqueId from 'lodash.uniqueid';
import ToDoForm from './components/TodoForm';

export default {
  name: 'App',
  components: {
    TodoList,
    ToDoForm
  },
  data() {
    return {
      TodoLists: [
        {id: uniqueId('todo-'), label: 'Learn Vue', done: false},
        {id: uniqueId('todo-'), label: 'Create a Vue project with the CLI', done: true},
        {id: uniqueId('todo-'), label: 'Have fun', done: true},
        {id: uniqueId('todo-'), label: 'Create a to-do list', done: false}
      ]
    };
  },
  methods: {
    addToDo(label) {
      this.TodoLists.unshift({id: uniqueId('todo-'), label: label, done: false})
    }
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
