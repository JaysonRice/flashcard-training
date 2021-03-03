<template>
  <section @click="handleClick">
    <p>{{ card.question }}</p>
    <p v-if="card.answerShown">{{ card.answer }}</p>
  </section>
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
section {
  height: 100%;
}
section:hover {
  cursor: pointer;
}
</style>
