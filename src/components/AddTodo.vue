<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="title">
    <button type="submit" class="create">Create</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: ''
    }
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false
        }

        this.$emit('add-todo', newTodo)
        this.title = ''
      }
    }
  }
}
</script>

<style scoped>
  form {
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    padding: .5rem .2rem;
    margin-bottom: .5rem;
  }

  input {
    width: 75%;
    border: none;
    margin-left: 10px;
  }

  .create {
    width: 20%;
    height: 25px;
    border: none;
    background:rgb(245, 72, 72);
    color: white;
  }
</style>
