<template>
  <form v-on:submit.prevent="onSubmit">
    <label for="new-todo-input">What needs to be done? </label>
    <input type="text" id="new-todo-input" name="new-todo" autocomplete="off"
           v-model.lazy.trim="ToDoName" class="input__lg"/>
    <button type="submit" class="btn btn__primary btn__lg">Add</button>
  </form>
</template>

<script>
export default {
  name: "ToDoForm",
  methods: {
    onSubmit() {
      console.log("form submitted: ", this.ToDoName)
      if (this.ToDoName === "") {
        alert("输入为空")
        return
      }
      this.$emit('todo-added', this.ToDoName)
      this.ToDoName = ""
    }
  },
  data() {
    return {
      ToDoName: "",
    }
  }
}
</script>

<style scoped>

</style>