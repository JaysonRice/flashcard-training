<template>
  <div>
    <h1>Star Wars Trivia</h1>
    <filter-buttons @difficulty="handleDifficultyFilter" />
    <div class="flashcardContainer">
      <div class="flashcardItem" v-for="question in trivia" :key="question.id">
        <flashcard-item :trivia="question" @answer-shown="handleAnswerStatus" />
      </div>
    </div>
  </div>
</template>

<script>
import TriviaItems from "../trivia";
import FlashcardItem from "./FlashcardItem.vue";
import FilterButtons from "./FilterButtons.vue";

export default {
  components: { FlashcardItem, FilterButtons },
  data() {
    return {
      trivia: [...TriviaItems],
    };
  },
  methods: {
    handleAnswerStatus(triviaItem) {
      triviaItem.answerShown = !triviaItem.answerShown;
    },

    handleDifficultyFilter(difficulty) {
      if (difficulty !== "all") {
        this.trivia = [...TriviaItems].filter(
          (q) => q.difficulty === difficulty
        );
      } else {
        this.trivia = [...TriviaItems];
      }
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
