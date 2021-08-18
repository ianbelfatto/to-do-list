<template>
  <div class="Todo">
    <h3>Todo List</h3>
    <form @submit.prevent="addTodo">
      <input v-model="newTodo" type="text" name="newTodo" id="newTodo" class="smallInput" />
      <button type="submit" name="button">Add Todo Item</button>
    </form>
    <button @click="allDone">Mark All Done</button>
    <br />
    <br />
    <p v-for="todo in todos" v-bind:key="todo">
      <input type="checkbox" v-model="todo.done" class="largerCheckbox" />
      &nbsp;
      <span :class="{ done: todo.done }">{{ todo.title }}</span>
      <br />
      <br />
      <button @click="removeTodo(todo)" class="smallButton">Remove</button>
    </p>
  </div>
</template>

<style>
/* .done {
  text-decoration: line-through;
}

body,
html {
  margin: 0 auto;
  max-width: 55em;
  line-height: 1.3;
}

.largerCheckbox {
  width: 20px;
  height: 20px;
}

p,
label,
button {
  font-family: "SF Mono";
} */

body {
  font-family: sans-serif;
  padding-top: 1em;
  padding-bottom: 1em;
  font-size: 1.5em;
  width: 35%;
  margin: 0 auto;
}
input,
textarea,
button,
p,
div,
section,
article,
select,
h3 {
  display: "block";
  width: 100%;
  font-family: "SF Mono", sans-serif;
  font-size: 0.9em;
  margin: 0.3em;
}

.smallButton {
  width: 60%;
}

.smallInput {
  display: block;
  width: 99%;
}

.largerCheckbox {
  width: 18px;
  height: 18px;
}

.done {
  text-decoration: line-through;
}
</style>

<script>
export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      newTodo: "",
      todos: [],
    };
  },
  created: function () {},
  methods: {
    addTodo() {
      this.todos.push({
        title: this.newTodo,
        done: false,
      });
      this.newTodo = "";
    },
    removeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },
    allDone() {
      this.todos.forEach((todo) => {
        todo.done = true;
      });
    },
  },
};
</script>
