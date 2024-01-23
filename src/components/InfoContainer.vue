<script setup>
import { onBeforeMount } from 'vue'

const props = defineProps({
  content: String,
  width: { type: String, default: '90px' }
})
</script>

<template>
  <div class="InfoContainer">
    <p class="info-container-content">{{ content }}</p>
  </div>
</template>

<style scoped>
.InfoContainer {
  display: flex;
  flex-direction: column;
  border-radius: 8px;
  background: var(--white-for-blur, rgba(232, 229, 218, 0.25));
  backdrop-filter: blur(2px);
  flex: 90px;
  height: 90px;
  min-width: 90px;
  width: v-bind(width);
  justify-content: center;
  align-content: center;
}

.info-container-content {
  height: min-content;
  width: 100%;
  color: var(--white, #e8e5da);
  text-align: center;
  font-family: Roboto;
  font-size: 20px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  letter-spacing: 4px;
}
</style>
