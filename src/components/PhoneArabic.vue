<script setup lang="ts">

function playSpeechSynthesis() {
  let utterance = new SpeechSynthesisUtterance("Hello world!");
  speechSynthesis.speak(utterance);
}

</script>

<template>
  <h1>Téléphone arabe</h1>
  <button @click="playSpeechSynthesis"></button>
</template>

<style scoped>

</style>
