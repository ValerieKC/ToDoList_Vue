<template>
  <div class="wrapper">
    <div class="title">Vue ToDo List</div>
    <div class="list-item-panel">
      <div class="list-todo-item" v-for="item in list" :item="item" :key="item.text">
        <div class="list-todo-text" :class="{strikeout:isDone}" @click="toggleDoneState">{{item.text}}</div>
        <button class="remove-todo-btn" @click="deleteItem(item.id)">-</button>
      </div>
    </div>
    <div class="input-panel">
      <input type="string" placeholder="I need to..." v-model="toDo">
      <button class="add-todo-btn" @click="createNewToDoItem">+</button>
    </div>
    <p>print:{{toDo}}</p>
  </div>
</template>

<script setup>

  import { ref } from "vue"
  import ToDoItem from "./ToDoItem.vue"

  const list = ref([])
  const isDone = ref(false)

  list.value.push({ id: 1, text: "clean the house" }, { id: 2, text: "buy milk" })
  const toDo = ref("")
  const generateId = () => {
    if (list.value && list.value.length) {
      return Math.max(...list.value.map((item) => item.id)) + 1
    } else {
      return 1
    }
  }

  const createNewToDoItem = () => {
    if (!toDo.value) return
    const newId = generateId()
    list.value.push({ id: newId, text: toDo.value })
    toDo.value = ""
  }

  const onDeleteItem = (id) => {
    console.log(id)
    list.value = list.value.filter(item => item.id !== id)
  }

  const toggleDoneState = () => {
    isDone.value = !isDone.value
    console.log("click")

  }

</script>

<style scope>
  .wrapper {
    width: 300px;
    margin: 0 auto;
  }

  .title {
    font-size: 28px;
    text-align: center;
  }

  .input-panel {
    width: 100%;
    display: flex;
  }

  input {
    width: 280px;
    margin-right: auto;
  }

  button {
    width: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 10px;
  }
</style>