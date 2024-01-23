<script setup>
import ImageContainer from './ImageContainer.vue'
import InfoContainer from './InfoContainer.vue'

const props = defineProps({ imgUrl: String, time: String, date: String })
</script>

<template>
  <div class="shot-details-big-container">
    <ImageContainer :src="imgUrl" width="310px" height="200px" class="image-shot-details" />
    <InfoContainer :content="time" class="time-container"></InfoContainer>
    <InfoContainer :content="date" class="date-container"></InfoContainer>
  </div>
</template>

<style>
.shot-details-big-container {
  height: 310px;
  width: 310px;
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  justify-content: start;
  flex-wrap: wrap;
  gap: 20px;
}
</style>
