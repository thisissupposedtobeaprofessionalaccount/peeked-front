<script setup>
const props = defineProps({
  src: String,
  width: { type: String, default: '145px' },
  height: { type: String, default: '145px' }
})
</script>

<template>
  <div class="shot">
    <img :src="src" />
  </div>
</template>

<style scoped>
.shot {
  width: v-bind(width);
  height: v-bind(height);
}
img {
  object-fit: cover;
  width: v-bind(width);
  height: v-bind(height);
  border-radius: 8px;
}
</style>
