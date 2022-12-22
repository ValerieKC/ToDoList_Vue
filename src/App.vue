<script setup>
  import ToDoVue from './components/ToDoVue.vue'
  import ToDoVue2 from './components/ToDoVue2.vue'

</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

  </header>

  <main>
    <ToDoVue />
    <!-- <ToDoVue2 /> -->

  </main>

</template>

<style scoped>
  header {
    line-height: 1.5;
  }

  .logo {
    display: block;
    margin: 0 auto 2rem;
  }
</style>