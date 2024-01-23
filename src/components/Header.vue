<script setup>
const props = defineProps({ content: String })
</script>

<template>
  <h2>
    <slot>Heading</slot>
  </h2>
</template>

<style scoped>
h2 {
  color: var(--transparent-white-for-text);
  margin-top: 10px;
  text-align: center;
  text-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  font-family: Roboto;
  font-weight: bold;
  font-size: 48px;
  font-style: normal;
  line-height: normal;
  letter-spacing: 14.4px;
  margin: 52px 40px 73px 40px;
  vertical-align: center;
  /*backdrop-filter: blur(2px);*/
}
</style>
