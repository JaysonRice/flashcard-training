<template>
  <div class="flashcardContainer">
    <div class="flashcardItem" v-for="question in trivia" :key="question.id">
      <flashcard-item :trivia="question" @answer-shown="handleAnswerStatus" />
    </div>
  </div>
</template>

<script>
import TriviaItems from "../trivia";
import FlashcardItem from "./FlashcardItem.vue";

export default {
  components: { FlashcardItem },
  data() {
    return {
      trivia: [...TriviaItems],
    };
  },
  methods: {
    handleAnswerStatus(triviaItem) {
      triviaItem.answerShown = !triviaItem.answerShown;
    },
  },
};
</script>

<style>
.flashcardContainer {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
.flashcardItem {
  border: 3px solid palegoldenrod;
  margin-top: 1em;
  margin-left: 1em;
  margin-right: 1em;
  width: 10em;
  height: 10em;
  background: lightgoldenrodyellow;
}
</style>
