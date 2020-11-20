<template>
  <div class="word" id="word"></div>
</template>

<script>
export default {
  name: "Word"
};
</script>

<style>
.word {
  display: flex;
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
}
</style>
