<template>
  <div class="popup-container" :style="{ display: display }">
    <div class="popup">
      <h2>{{ message }}</h2>
      <h3 v-if="status === 'lose'">{{ revealWord }}</h3>
      <button @click="$emit('play-again')">Play Again</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Popup",
  computed: {
    message: function() {
      return this.status === "win"
        ? "Congratulations! You won!"
        : "Unfortunately you lost.";
    },
    revealWord: function() {
      return `The word was: ${this.selectedWord}`;
    },
    display: function() {
      return this.status === "win" || this.status === "lose" ? "flex" : "none";
    }
  },
  props: {
    selectedWord: {
      type: String,
      required: true
    },
    status: {
      type: String,
      required: true
    }
  }
};
</script>

<style>
.popup-container {
  background-color: rgba(0, 0, 0, 0.3);
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  display: none;
  align-items: center;
  justify-content: center;
}

.popup {
  background: #fefefe;
  border-radius: 5px;
  box-shadow: 0 15px 10px 3px rgba(0, 0, 0, 0.1);
  padding: 20px;
  text-align: center;
}

.popup button {
  cursor: pointer;
  background-color: #f15032;
  color: #fefefe;
  border: 0;
  margin-top: 20px;
  padding: 12px 20px;
  font-size: 16px;
  border-radius: 5px;
  transition: all 200ms ease-in-out;
}

.popup button:hover {
  background-color: #fefefe;
  color: #f15032;
}

.popup button:active {
  transform: scale(0.98);
}

.popup button:focus {
  outline: 0;
}
</style>
