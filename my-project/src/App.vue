<template>
  <div id="app">
    <Header/>
    <AddTodo/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
//import Header from './components/Header';
import AddTodo from './components/AddTodo';
import Todos from './components/Todos';
import Header from "@/components/Header";

export default {
  name: "app",
  components: {
    Header,
    Todos,
    AddTodo
  },
  data(){
    return {
      todos: [
        {id: 1,
          title: "Todo One",
          completed: false},
        {id: 2,
          title: "Todo Two",
          completed: true},
        {id: 3,
          title: "Todo Three",
          completed: false}
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    }
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
