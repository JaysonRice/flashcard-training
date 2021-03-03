<template>
  <div>
    <button @click="handleClick('easy')">Easy</button>
    <button @click="handleClick('medium')">Medium</button>
    <button @click="handleClick('hard')">Hard</button>
    <button @click="handleClick('all')">All</button>
  </div>
</template>

<script>
export default {
  methods: {
    handleClick(selected) {
      this.$emit("difficulty", selected);
    },
  },
};
</script>

<style></style>
