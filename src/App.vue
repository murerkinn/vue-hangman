<template>
  <Header />
  <div class="game-container">
    <Figure :wrongLetters="wrongLetters" />
    <WrongLetters :wrongLetters="wrongLetters" />
    <Word :selectedWord="selectedWord" :correctLetters="correctLetters" />
  </div>
  <Popup
    :status="status"
    :selectedWord="selectedWord"
    @play-again="playAgain"
  />
  <Notification :not="notification" />
  <span class="footer">
    @2020 - Made by Murat Erkin Cicek with ❤️ | View on
    <a href="https://github.com/murerkinn/vue-hangman" target="_blank">
      Github
    </a>
  </span>
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
      selectedWord: "",
      playable: true,
      correctLetters: [],
      wrongLetters: [],
      notification: false,
      status: ""
    };
  },
  computed: {
    sizeOfSelectedWordSet: function() {
      const set = new Set(this.selectedWord.split(""));
      return set.size;
    }
  },
  methods: {
    selectWord() {
      this.selectedWord = this.words[
        Math.floor(Math.random() * this.words.length)
      ];
    },
    handleKeyDown(e) {
      const { key, keyCode } = e;
      const forbiddens = [8, 9, 16, 17, 18, 20, 37, 38, 39, 40];
      const regex = /[a-zA-Z]/;
      if (this.playable && regex.test(key) && !forbiddens.includes(keyCode)) {
        const letter = key.toLowerCase();

        if (this.selectedWord.includes(letter)) {
          if (!this.correctLetters.includes(letter)) {
            this.correctLetters.push(letter);
          } else {
            this.showNotification();
          }
        } else {
          if (!this.wrongLetters.includes(letter)) {
            this.wrongLetters.push(letter);
          } else {
            this.showNotification();
          }
        }

        this.checkWin();
      }
    },
    showNotification() {
      this.notification = true;

      setTimeout(() => {
        this.notification = false;
      }, 2000);
    },
    checkWin() {
      // check for win
      if (this.sizeOfSelectedWordSet === this.correctLetters.length) {
        this.playable = false;
        this.status = "win";
      }

      // check for lose
      if (this.wrongLetters.length === 6) {
        this.playable = false;
        this.status = "lose";
      }
    },
    playAgain() {
      // you can set everything to their first values and select another random word
      /* this.playable = true;
         this.status = "";
         this.correctLetters = [];
         this.wrongLetters = [];
         this.selectWord(); */

      // or you can just refresh the page
      location.reload();
      return false;
    }
  },
  created() {
    this.selectWord();
    this.checkWin();
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

.footer {
  position: absolute;
  bottom: 30px;
}
</style>
