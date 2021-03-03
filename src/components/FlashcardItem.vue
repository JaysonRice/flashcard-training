<template>
  <section @click="handleClick">
    <p>{{ trivia.question }}</p>
    <p v-if="trivia.answerShown">{{ trivia.answer }}</p>
  </section>
</template>

<script>
export default {
  props: ["trivia"],

  methods: {
    handleClick() {
      this.$emit("answer-shown", this.trivia);
    },
  },
};
</script>

<style scoped>
section {
  height: 100%;
}
</style>
