<template>
  <div id="app">
    <Header/>
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import AddTodo from "./components/AddTodo";
import Todos from "./components/Todos";
import Header from "@/components/Header";
import axios from "axios";
export default {
  name: "app",
  components: {
    Header,
    Todos,
    AddTodo
  },
  data(){
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
      axios.delete('https://jsonplaceholder.typicode.com/todos/${id}').catch(err => console.log(err));
      this.todos = this.todos.filter(todo => todo.id !== id);
    }, //.then(res => this.todos = this.todos.filter(todo => todo.id !== id))
    addTodo(newTodo) {
      const { title, completed } = newTodo;

      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
      completed
      }).then(res => this.todos = [...this.todos, res.data]).catch(err => console.log(err));
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10').then(res => this.todos = res.data).catch(err => console.log(err));
  }
}

</script>
<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
