<script setup lang="ts">
import { ref } from "vue";

const text = ref("");

function playSpeechSynthesis() {
  let utterance = new SpeechSynthesisUtterance(text.value);
  speechSynthesis.speak(utterance);
}

</script>

<template>
  <h1>Téléphone arabe</h1>
  <form @submit.prevent="playSpeechSynthesis">
    <input v-model="text" type="text" />
    <button type="submit">submit</button>
  </form>
</template>

<style scoped>

</style>
