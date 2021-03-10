<template>
  <div>
    <h1>Star Wars Trivia</h1>
    <div class="triviaControls">
      <filter-buttons @difficulty="handleDifficultyFilter" />
      <h3 class="hide-button" @click="handleHideAll">Hide All Answers</h3>
    </div>
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
@import url("https://fonts.googleapis.com/css2?family=Poller+One&display=swap");
h1 {
  font-family: "Poller One", cursive;
  font-size: 4vw;
  margin-bottom: 0;
  -webkit-text-stroke-width: 1px;
  -webkit-text-stroke-color: #23415f;
}
.flashcardContainer {
  display: flex;
  justify-content: space-evenly;
  flex-wrap: wrap;
}
.triviaControls {
  display: flex;
  width: 50%;
  margin: 0 auto;
  justify-content: space-evenly;
  align-items: center;
}
.hide-button:hover {
  cursor: pointer;
  color: palegoldenrod;
}
</style>
