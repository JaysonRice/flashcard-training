<template>
  <div id="app">
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
body {
  background-color: whitesmoke;
  background-image: url("https://cdn.pixabay.com/photo/2018/08/15/13/10/galaxy-3608029_1280.jpg");
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #efd469;
  margin-top: 60px;
}
</style>
