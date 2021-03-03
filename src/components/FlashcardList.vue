<template>
  <div>
    <h1>Star Wars Trivia</h1>
    <h3 class="hide-button" @click="handleHideAll">Hide All Answers</h3>
    <filter-buttons @difficulty="handleDifficultyFilter" />
    <div class="flashcardContainer">
      <div class="flashcardItem" v-for="card in displayedTrivia" :key="card.id">
        <flashcard-item :card="card" @answer-shown="handleAnswerStatus" />
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
      selectedDifficulty: "all",
    };
  },
  methods: {
    handleAnswerStatus(triviaItem) {
      triviaItem.answerShown = !triviaItem.answerShown;
    },

    handleDifficultyFilter(difficulty) {
      this.selectedDifficulty = difficulty;
    },
    handleHideAll() {
      this.trivia.forEach((card) => {
        card.answerShown = false;
      });
    },
  },
  computed: {
    displayedTrivia() {
      if (this.selectedDifficulty === "all") {
        return this.trivia;
      }
      return this.trivia.filter(
        (t) => t.difficulty === this.selectedDifficulty
      );
    },
  },
};
</script>

<style>
.flashcardContainer {
  display: flex;
  justify-content: space-evenly;
  flex-wrap: wrap;
}
.flashcardItem {
  border: 3px solid palegoldenrod;
  margin-top: 1em;
  width: 10em;
  height: 10em;
  background: lightgoldenrodyellow;
}
.hide-button:hover {
  cursor: pointer;
  color: navy;
}
</style>
