<template>
  <div id="app">
    <Todos v-bind:todos="todos"/>
  </div>
</template>

<script>
import Todos from './components/Todos';

export default {
  name: "app",
  components: {
    Todos
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
  }

}</script>
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
