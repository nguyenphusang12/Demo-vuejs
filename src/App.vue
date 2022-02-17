<template>
  <div id="app">
    <ToDoApp />
  </div>
</template>

<script>
import ToDoApp from "./components/ToDoApp.vue";

export default {
  name: "App",
  components: {
    ToDoApp,
  },
};
</script>

<style >
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
</style>
