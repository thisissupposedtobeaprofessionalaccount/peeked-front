<script setup>
import ImageContainer from '@/components/ImageContainer.vue'
import ShotDetails from '@/components/ShotDetails.vue'
import ShotDetailsBig from '@/components/ShotDetailsBig.vue'
import ButtonImage from '@/components/ButtonImage.vue'
import Header from '@/components/Header.vue'
import InfoContainer from '@/components/InfoContainer.vue'
import { onMounted, watch, ref } from 'vue'

const shots = ref([])

onMounted(() => {
  fetch('http://' +  import.meta.env.VITE_BACKENDURL  + '/gallery').then((res) => {
    res.json().then((value) => {
      shots.value.push(
        ...value.map((img) => {
          const msSincEpoch = Number(img.slice(0, -4))
          var date = new Date(msSincEpoch)
          getDateDisplay(date)
          return {
            url: 'http://' + import.meta.env.VITE_BACKENDURL  + '/gallery/' + img,
            time: getHourDisplay(date),
            date: getDateDisplay(date)
          }
        })
      )
    })
  })
})

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
</script>

<template>
  <Header>GALLERY</Header>
  <main class="gallery-content" v-if="shots.length !== 0">
    <div class="stat-grid">
      <InfoContainer></InfoContainer>
    </div>
    <ShotDetailsBig
      :img-url="shots[0].url"
      :time="shots[0].time"
      :date="shots[0].date"
    ></ShotDetailsBig>

    <ShotDetails
      v-for="(shot, index) in shots.slice(1)"
      :img-url="shot.url"
      :time="shot.time"
      :date="shot.date"
      :wrap="index % 2 == 0 ? 'wrap' : 'wrap-reverse'"
    />
  </main>
  <main v-else>
    <InfoContainer content=" &#160 Datas not fetched yet &#160" width="100%"></InfoContainer>
  </main>
</template>

<style>
.gallery-content {
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
