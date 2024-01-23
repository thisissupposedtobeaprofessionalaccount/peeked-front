<script setup>
import ImageContainer from '@/components/ImageContainer.vue'
import ShotDetails from '@/components/ShotDetails.vue'
import ButtonImage from '@/components/ButtonImage.vue'
import Header from '@/components/Header.vue'
import { ref, watch } from 'vue'
import { onBeforeMount, onMounted } from 'vue'

const lastThreeImagesUrl = ref([])
const lastImageDate = ref(getDateDisplay(new Date()))
const lastImageTime = ref(getHourDisplay(new Date()))

function getHourDisplay(shotDate) {
  return (
    shotDate.getHours().toString().padStart(2, '0') +
    ':' +
    shotDate.getMinutes().toString().padStart(2, '0')
  )
}

function getDateDisplay(shotDate) {
  return (
    shotDate.getDay().toString().padStart(2, '0') +
    '/' +
    (shotDate.getMonth() + 1).toString().padStart(2, '0')
  )
}

onMounted(() => {
  fetch('http://' + 'peeked-back:3010' + '/recent?n=3').then((res) => {
    res.json().then((value) => {
      console.log('PROUTE')
      const date = new Date(Number(value[0].slice(0, -4)))
      lastImageDate.value = getHourDisplay(date)
      lastImageTime.value = getDateDisplay(date)
      value.forEach((element, index) => {
        lastThreeImagesUrl.value[index] = 'http://' + 'localhost:3010' + '/gallery/' + element
      })
    })
  })
})
</script>

<template>
  <Header>PEEKED</Header>
  <main class="home-content" v-if="lastImageDate !== undefined">
    <ShotDetails
      :img-url="lastThreeImagesUrl[0]"
      :time="lastImageTime"
      :date="lastImageDate"
    ></ShotDetails>
    <div class="previous-shot-row">
      <ImageContainer :src="lastThreeImagesUrl[1]"></ImageContainer>
      <ImageContainer :src="lastThreeImagesUrl[2]"></ImageContainer>
    </div>
    <ButtonImage :src="lastThreeImagesUrl[1]" @click="$router.push('/gallery')"></ButtonImage>
  </main>
</template>

<style>
.home-content {
  width: 310px;
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  justify-content: flex-start;
  align-content: flex-start;
  gap: 20px;
  margin-bottom: 129px;
}

.previous-shot-row {
  display: flex;
  flex-direction: row;
  gap: 20px;
}
</style>
