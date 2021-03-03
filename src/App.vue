<template>
  <div id="app">
    <h1>Star Wars Trivia</h1>

    <flashcard-list />
  </div>
</template>

<script>
import FlashcardList from "./components/FlashcardList.vue";

export default {
  name: "App",
  components: {
    FlashcardList,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
