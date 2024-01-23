<script setup>
const props = defineProps({ src: String })
</script>

<template>
  <div class="button-image">
    <img :src="src" />
    <div class="button-filter">
      <p>GALLERY</p>
    </div>
  </div>
</template>

<style scoped>
.shot {
  width: v-bind(size);
  height: v-bind(size);
}
.button-image {
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: 1fr;
}
img {
  grid-row: 1;
  grid-column: 1;
  object-fit: cover;
  width: 100%;
  height: 145px;
  border-radius: 8px;
}
.button-filter {
  grid-row: 1;
  grid-column: 1;
  width: 100%;
  height: 100%;
  z-index: 1;
  border-radius: 8px;
  background: rgba(10, 52, 49, 0.2);
  backdrop-filter: blur(6px);
  -webkit-backdrop-filter: blur(6px);
  backdrop-filter: blur(6px);
  display: flex;
  flex-direction: column;
  align-content: center;
  justify-content: center;
}
.button-filter > p {
  color: var(--white, #e8e5da);
  text-align: center;
  font-family: Roboto;
  font-size: 20px;
  font-style: normal;
  font-weight: 700;
  line-height: normal;
  letter-spacing: 4px;
  text-align: center;
}
</style>
