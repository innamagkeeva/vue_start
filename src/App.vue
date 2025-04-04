<script setup lang="ts">
type ButtonBase = {
  id: number
  text: string
}

const arrayOfLetters: ButtonBase[] = [
  {
    id: 0,
    text: 'A',
  },
  {
    id: 1,
    text: 'B',
  },
  {
    id: 2,
    text: 'C',
  },
  {
    id: 3,
    text: 'D',
  },
  {
    id: 4,
    text: 'E',
  },
  {
    id: 5,
    text: 'F',
  },
  {
    id: 6,
    text: 'G',
  },
  {
    id: 7,
    text: 'H',
  },
  {
    id: 8,
    text: 'I',
  },
  {
    id: 9,
    text: 'J',
  },
  {
    id: 10,
    text: 'K',
  },
  {
    id: 11,
    text: 'L',
  },
  {
    id: 12,
    text: 'M',
  },
  {
    id: 13,
    text: 'N',
  },
  {
    id: 14,
    text: 'O',
  },
  {
    id: 15,
    text: 'P',
  },
  {
    id: 16,
    text: 'Q',
  },
  {
    id: 17,
    text: 'R',
  },
  {
    id: 18,
    text: 'S',
  },
  {
    id: 19,
    text: 'T',
  },
  {
    id: 20,
    text: 'U',
  },
  {
    id: 21,
    text: 'V',
  },
  {
    id: 22,
    text: 'W',
  },
  {
    id: 23,
    text: 'X',
  },
  {
    id: 24,
    text: 'Y',
  },
  {
    id: 25,
    text: 'Z',
  },

  {
    id: 26,
    text: ' ',
  },
  {
    id: 27,
    text: '.',
  },
  {
    id: 28,
    text: ',',
  },
  {
    id: 29,
    text: '!',
  },
  {
    id: 30,
    text: '?',
  },
]

import { ref } from 'vue'
const result = ref(' ')

function getResult(str: string): void {
  console.log(str)

  result.value += str
}

function deleteSign(): void {
  result.value = result.value.slice(0, -1)
}
</script>

<template>
  <ul class="button">
    <li
      class="button__li"
      v-for="element in arrayOfLetters"
      :key="element.id"
      @click="getResult(element.text)"
    >
      <p class="button__name">{{ element.text }}</p>
    </li>
  </ul>
  <button class="btn__delete" @click="deleteSign">DELETE</button>
  <h1 class="result">{{ result }}</h1>
</template>

<style>
.button {
  list-style: none;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

.button__li,
.btn__delete {
  margin: 10px;
  background-color: green;
  height: 60px;
  border: none;
  border-radius: 20px;
  color: white;
  font-size: 20px;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
}

.button__li {
  width: 50px;
}

.btn__delete {
  width: 100px;
}

.button__name {
  font-size: 40px;
}

/* .button_space {
  height: 30px;
} */
</style>
