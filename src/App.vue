<script setup>
import { ref } from 'vue'
</script>

<template>
  <div class="center-content">
    <RouterView />
  </div>
</template>

<style>
body {
  padding: 0;
  background:
    url(assets/bg_noise.png),
    var(--bg-gradient) no-repeat;
  height: 100vh;
  background-attachment: fixed;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
}
/* styles.css (ou styles.scss) */
.center-content {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
