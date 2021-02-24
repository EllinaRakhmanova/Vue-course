<template>
  <li>
    <span v-bind:class="{done: todo.completed}">
      <input type="checkbox" 
              v-on:change="todo.completed = !todo.completed">
      <strong>{{index + 1}}</strong>
      {{todo.title}}
    </span>
    <button class="db" 
            v-on:click="$emit('remove-todo', todo.id)"
    >&times;</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    },
    index: Number
  }
}
</script>

<style scoped>
  li {
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    padding: .5rem .2rem;
    margin-bottom: 1rem;
  }

  .db {
    background: lightslategrey;
    color: #fff;
    border-radius: 50%;
    font-weight: bold;
  }

  input {
    margin-right: 1rem;
  }

  .done {
    text-decoration: line-through;
  }
</style>