<template>
  <Header />
  <div class="game-container">
    <Figure />
    <WrongLetters :wrongLetters="wrongLetters" />
    <Word :selectedWord="selectedWord" :correctLetters="correctLetters" />
  </div>
  <Popup />
  <Notification />
</template>

<script>
import Header from "@/components/Header";
import Figure from "@/components/Figure";
import WrongLetters from "@/components/WrongLetters";
import Word from "@/components/Word";
import Popup from "@/components/Popup";
import Notification from "@/components/Notification";

export default {
  name: "App",
  components: {
    Header,
    Figure,
    WrongLetters,
    Word,
    Popup,
    Notification
  },
  data() {
    return {
      words: ["composition", "hangman", "development", "framework"],
      playable: true,
      correctLetters: [],
      wrongLetters: []
    };
  },
  computed: {
    selectedWord() {
      return this.words[Math.floor(Math.random() * this.words.length)];
    }
  },
  methods: {
    handleKeyDown(e) {
      const { key, keyCode } = e;
      if (this.playable && keyCode >= 65 && keyCode <= 90) {
        const letter = key.toLowerCase();

        if (this.selectedWord.includes(letter)) {
          if (!this.correctLetters.includes(letter)) {
            this.correctLetters.push(letter);
          } else {
            // this.showNotification();
          }
        } else {
          if (!this.wrongLetters.includes(letter)) {
            this.wrongLetters.push(letter);
          } else {
            // this.showNotification();
          }
        }
      }
    }
    // showNotification() {
    //   Notification.classList.add("show");

    //   setTimeout(() => {
    //     Notification.classList.remove("show");
    //   }, 2000);
    // }
  },
  mounted() {
    window.addEventListener("keydown", this.handleKeyDown);
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  background-color: #fefefe;
  color: #222;
  font-family: sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100vh;
  overflow: hidden;
}

.game-container {
  padding: 20px 30px;
  position: relative;
  margin: auto;
  height: 350px;
  width: 450px;
}
</style>
