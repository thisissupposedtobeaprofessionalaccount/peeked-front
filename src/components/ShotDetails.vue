<script setup>
import ImageContainer from './ImageContainer.vue'
import InfoContainer from './InfoContainer.vue'

const props = defineProps({
  imgUrl: String,
  wrap: { type: String, default: 'wrap' },
  time: String,
  date: String
})
</script>

<template>
  <div class="shot-details-container">
    <ImageContainer :src="imgUrl" width="200px" height="200px" class="image-shot-details" />
    <InfoContainer :content="time" class="time-container"></InfoContainer>
    <InfoContainer :content="date" class="date-container"></InfoContainer>
  </div>
</template>

<style>
.shot-details-container {
  height: 200px;
  width: 310px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: start;
  flex-wrap: v-bind(wrap);
  gap: 20px;
}
</style>
