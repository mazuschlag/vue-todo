<template>
  <div id="app">
    <!-- Bind todos data to a prop called 'todos' -->
    <todo-list v-bind:todos="todos"></todo-list>
    <!-- When a todo emits 'add-todo', execute the method 'addTodo' -->
    <create-todo v-on:create-todo="createTodo"></create-todo>
  </div>
</template>

<script type="text/javascript">
import TodoList from './components/TodoList';
import CreateTodo from './components/CreateTodo';

export default {
  name: 'App',
  components: {
    TodoList,
    CreateTodo,
  },
  // Building props to send to ToDoList
  data() {
    return {
      /*todos: [{
        title: 'Todo A',
        project: 'Project A',
        done: false,
        id: 0,
      }, {
        title: 'Todo B',
        project: 'Project B',
        done: true,
        id: 1,
      }, {
        title: 'Todo C',
        project: 'Project C',
        done: false,
        id: 2,
      }, {
        title: 'Todo D',
        project: 'Project D',
        done: false,
        id: 3,
      }],*/
      todos: [],
    };
  },
  methods: {
    createTodo(todo) {
      this.todos.push(todo);
    },
  },
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
</style>
