<template>
  <div class="list-todo-item">
    <div class="list-todo-text" :class="{strikeout:isDone}" @click="toggleDoneState">{{item.text}}</div>
    <button class="remove-todo-btn" @click="deleteItem(item.id)">-</button>
  </div>
</template>

<script>
  import { ref } from "vue"

  export default {
    name: "ToDoItem",
    props: ["item"],
    setup(props, { emit }) {
      function deleteItem(id) {
        emit("delete", id)
      }
      const isDone = ref(false)
      const toggleDoneState = () => {
        isDone.value = !isDone.value
        console.log("click")

      }
      return {
        deleteItem,
        isDone,
        toggleDoneState
      }
    }
  };
</script>

<style>
  .list-todo-item {
    display: flex;
    width: 300px;
    justify-content: space-between;
  }

  .list-todo-text {
    width: 100%;
  }

  .strikeout {
    text-decoration: line-through;
  }
</style>