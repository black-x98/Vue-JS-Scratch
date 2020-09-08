<template>
  <div>
    <h1>HEADER</h1>
    <div v-bind:key="todo.id" v-for="todo in todos">
      <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)"/>
    </div>
    <footer>This is the footer.</footer>
  </div>
</template>

<script>
import TodoItem from "@/components/TodoItem";

export default {
name: "Todos",
  components: {
    TodoItem
  },
  props: ["todos"]
}

</script>

<style scoped>

</style>