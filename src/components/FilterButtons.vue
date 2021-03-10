<template>
  <div>
    <button
      :class="{ chosen: chosenDifficulty === 'easy' }"
      @click="handleClick('easy')"
    >
      Easy
    </button>
    <button
      :class="{ chosen: chosenDifficulty === 'medium' }"
      @click="handleClick('medium')"
    >
      Medium
    </button>
    <button
      :class="{ chosen: chosenDifficulty === 'hard' }"
      @click="handleClick('hard')"
    >
      Hard
    </button>
    <button
      :class="{ chosen: chosenDifficulty === 'all' }"
      @click="handleClick('all')"
    >
      All
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      chosenDifficulty: "all",
    };
  },
  methods: {
    handleClick(selected) {
      this.chosenDifficulty = selected;
      this.$emit("difficulty", selected);
    },
  },
};
</script>

<style scoped>
button {
  padding: 0.5em;
  margin-left: 0.5rem;
  margin-right: 0.5rem;
  border: #23415f solid 2px;
  color: #23415f;
  background-color: whitesmoke;
  width: 5em;
  border-radius: 0.5em;
}

button:hover {
  cursor: pointer;
}

button.chosen {
  background-color: palegoldenrod;
}
</style>
