<template>
  <Header />
  <div class="game-container">
    <Figure />
    <WrongLetters />
    <Word />
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
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  background-color: #fefefe;
  color: #222;
  font-family: sans-serif;
  display: flex;
  flex-direction: column;
  justify-content: center;
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

.letter {
  border-bottom: 3px solid #2980b9;
  display: inline-flex;
  font-size: 30px;
  align-items: center;
  justify-content: center;
  margin: 0 3px;
  height: 50px;
  width: 20px;
}
</style>
