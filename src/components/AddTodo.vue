<template>
  <form @submit.prevent="onSubmit">
    <label>
      <input v-model="title" type="text">
    </label>
    <button type= "submit" >Create</button>
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
          completed : false
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
    display: flex;
  }
  input{
    width: 500px;
  }
</style>