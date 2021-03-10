<template>
  <div class="card" :class="{ flipped: card.answerShown }" @click="handleClick">
    <p v-if="!card.answerShown">{{ card.question }}</p>
    <p v-if="card.answerShown">{{ card.answer }}</p>
  </div>
</template>

<script>
export default {
  props: ["card"],

  methods: {
    handleClick() {
      this.$emit("answer-shown", this.card);
    },
  },
};
</script>

<style scoped>
.card {
  border: 4px solid #efd469;
  margin-top: 1em;
  width: 10em;
  height: 10em;
  margin: 0.5em;
  padding: 0.5em;
  background: #23415f;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 1em;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 2px 4px rgba(0, 0, 0, 0.582);
}
.card:hover {
  cursor: pointer;
  background-color: #36587a;
}
.flipped {
  color: #23415f;
  border: 4px solid #23415f;
  background-color: #efd469;
}
.flipped:hover {
  background-color: #efd469;
}
</style>
