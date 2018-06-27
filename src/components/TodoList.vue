<!-- Visual part of component -->
<template>
  <div>
    <!-- JS expressions in Vue are enclosed in double curly brackets -->
    <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    <!-- When a todo emits 'complete-todo', execute the method 'completeTodo' -->
    <!-- When a todo emits 'delete-todo', execute the method 'deleteTodo.' -->
    <!-- Iterate through todos prop (each item is a 'todo' object from App.vue) -->
    <!-- When iterating, must give children a unique key (id) -->
    <!-- Pass the todo object from the todos prop to the prop 'todo' -->
    <todo v-on:complete-todo="completeTodo" v-on:delete-todo="deleteTodo" v-for="todo in todos" v-bind:key="todo.id" v-bind:todo="todo"></todo>
  </div>
</template>

<!-- Behavior, events, and data storage -->
<script type="text/javascript" >

import Todo from './Todo';

export default {
  // ['name of prop being passed', 'name of other prop being passed (?)']
  props: ['todos'],
  // Components that this component will render
  components: {
    Todo,
  },
  // Methods that this component will use
  methods: {
    deleteTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },
    completeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = true;
    },
  },
};

</script>

<!-- Improve appearance -->
<style>
</style>
