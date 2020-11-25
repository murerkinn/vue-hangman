<template>
  <div :class="[{ show: not }, 'notification-container']">
    <p>You have already entered this letter</p>
  </div>
</template>

<script>
export default {
  name: "Notification",
  props: {
    not: {
      type: Boolean,
      required: true
    }
  }
};
</script>

<style>
.notification-container {
  background-color: rgba(0, 0, 0, 0.3);
  border-radius: 10px 10px 0 0;
  padding: 15px 20px;
  position: absolute;
  bottom: -50px;
  transition: transform 0.3s ease-in-out;
}

.notification-container p {
  margin: 0;
}

.notification-container.show {
  transform: translateY(-50px);
}
</style>
