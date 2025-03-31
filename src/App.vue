<script setup lang="ts">
// import { ref } from 'vue'

// let result = ref('')

// function getResult(){
//   result.value +=
// }
</script>

<template>
  <button class="button" @click="getResult()">A</button>
  <button class="button" @click="getResult()">B</button>
  <button class="button" @click="getResult()">C</button>
  <button class="button" @click="getResult()">D</button>
  <button class="button" @click="getResult()">F</button>
  <button class="button" @click="getResult()">G</button>
  <button class="button" @click="getResult()">H</button>
  <button class="button" @click="getResult()">I</button>
  <button class="button" @click="getResult()">J</button>
  <button class="button" @click="getResult()">K</button>
  <button class="button" @click="getResult()">L</button>
  <button class="button" @click="getResult()">M</button>
  <button class="button" @click="getResult()">N</button>
  <button class="button" @click="getResult()">O</button>
  <button class="button" @click="getResult()">P</button>
  <button class="button" @click="getResult()">Q</button>
  <button class="button" @click="getResult()">R</button>
  <button class="button" @click="getResult()">S</button>
  <button class="button" @click="getResult()">T</button>
  <button class="button" @click="getResult()">U</button>
  <button class="button" @click="getResult()">V</button>
  <button class="button" @click="getResult()">W</button>
  <button class="button" @click="getResult()">X</button>
  <button class="button" @click="getResult()">Y</button>
  <button class="button" @click="getResult()">Z</button>
  <button class="button_space" @click="getResult()"></button>
  <button class="button" @click="getResult()">.</button>
  <button class="button" @click="getResult()">,</button>
  <button class="button" @click="getResult()">!</button>
  <button class="button" @click="getResult()">?</button>
  <button class="button_delete" @click="getResult()">DELETE</button>
  <h1 class="result">{{ result }}</h1>
</template>

<style>
button {
  margin: 10px;
  background-color: green;
  height: 60px;
  width: 50px;
  border: none;
  border-radius: 20px;
  color: white;
  font-size: 20px;
  cursor: pointer;
}

.button_space {
  height: 30px;
}

.button_delete {
  width: 100px;
}
</style>
