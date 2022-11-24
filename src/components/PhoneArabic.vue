<script setup lang="ts">
import { ref } from "vue";

const text = ref("");

/*const listWords = [
  "Astrologie",
  "Manteau",
  "Téléphone",
  "Ordinateur",
  "Chargeur",
  "Voiture",
  "Lune",
  "Planète",
  "Lunettes"
];

function playSpeechRandom() {
  const randomWords = listWords[Math.floor(Math.random()*listWords.length)];
  const speechRandom = new SpeechSynthesisUtterance(randomWords);
  speechSynthesis.speak(speechRandom);
} */

function playSpeechSynthesis() {

  const recognition = new webkitSpeechRecognition();
//recognition.continuous = false;
  recognition.lang = 'fr-FR';
  recognition.interimResults = false;
  recognition.maxAlternatives = 1;

  recognition.start();

  recognition.onresult = function(event) {
    const resultEvent = event.results[0][0].transcript;
    const divResult = document.getElementById("result-voice")!;
    const sentence = resultEvent.replaceAll("quoi", "feur").replaceAll("tu", "je").replaceAll("vas", "vais");
    const utterance = new SpeechSynthesisUtterance(sentence);
    speechSynthesis.speak(utterance);
    divResult.innerHTML = sentence;
    recognition.stop();
  }

}


</script>

<template>
  <h1>Téléphone arabe</h1>
  <form @submit.prevent="playSpeechSynthesis">
    <button type="submit">submit</button>
  </form>
  <div id="result-voice"></div>
  <!--<button type="submit" @click="playSpeechRandom">Mots aléatoire</button> -->
</template>

<style scoped>

</style>
