<template>
  <svg height="375" width="300" class="figure-container">
    <!-- Rod -->
    <line x1="135" y1="40" x2="210" y2="40" />
    <line x1="210" y1="40" x2="210" y2="75" />
    <line x1="135" y1="40" x2="135" y2="345" />
    <line x1="40" y1="345" x2="175" y2="345" />

    <!-- Head -->
    <circle cx="210" cy="105" r="40" class="figure-part" />
    <!-- Body -->
    <line x1="210" y1="135" x2="210" y2="175" class="figure-part" />
    <!-- Arms -->
    <line x1="210" y1="140" x2="140" y2="175" class="figure-part" />
    <line x1="210" y1="140" x2="1135" y2="175" class="figure-part" />
    <!-- Legs -->
    <line x1="210" y1="175" x2="140" y2="270" class="figure-part" />
    <line x1="210" y1="175" x2="1135" y2="270" class="figure-part" />
  </svg>
</template>

<script>
export default {
  name: "Figure"
};
</script>

<style>
.figure-container {
  fill: transparent;
  stroke: #222;
  stroke-width: 6px;
  stroke-linecap: round;
}

.figure-part {
  display: none;
}
</style>
