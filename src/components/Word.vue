<template>
  <div class="word" id="word">
    <span class="letter" v-for="(char, index) in word" :key="index">
      {{ correctLetters.includes(char) ? char : "" }}
    </span>
  </div>
</template>

<script>
export default {
  name: "Word",
  props: {
    selectedWord: {
      type: String,
      required: true
    },
    correctLetters: {
      type: Array,
      required: true
    }
  },
  computed: {
    word() {
      return this.selectedWord.split("");
    }
  }
};
</script>

<style>
.word {
  display: flex;
}

.letter {
  border-bottom: 3px solid #f15032;
  display: inline-flex;
  font-size: 30px;
  align-items: center;
  justify-content: center;
  margin: 0 3px;
  height: 50px;
  width: 20px;
}
</style>
