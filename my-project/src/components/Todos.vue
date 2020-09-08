<template>
  <div>
    <h1>HEADER</h1>
    <div v-bind:key="todo.id" v-for="todo in todos">
      <h3>{{todo.title}}</h3>
    </div>
    <footer>This is the footer.</footer>
  </div>
</template>

<script>
//import TodoItem from "@/components/TodoItem";

export default {
name: "Todos",
  props: ["todos"]
}

</script>

<style scoped>

</style>