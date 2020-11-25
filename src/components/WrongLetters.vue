<template>
  <div class="wrong-letters-container">
    <div>
      <p v-if="wrongLetters.length">Wrong</p>
      <span v-for="(letter, index) in wrongLetters" :key="index">
        {{ letter }},
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: "WrongLetters",
  props: {
    wrongLetters: {
      type: Array,
      required: true
    }
  }
};
</script>

<style>
.wrong-letters-container {
  position: absolute;
  top: 20px;
  right: 20px;
  display: flex;
  flex-direction: column;
  text-align: right;
}

.wrong-letters-container p {
  margin: 0 0 5px;
}

.wrong-letters-container span {
  font-size: 24px;
}
</style>
