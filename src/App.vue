<script setup lang="ts">
import { ref } from 'vue'

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
  <ul class="list">
    <li
      class="list__li"
      v-for="element in arrayOfLetters"
      :key="element.id"
    >
      <button
        class="list__button-name"
        @click="getResult(element.text)"
      >
        {{ element.text }}
      </button>
    </li>
  </ul>
  <button
    class="list__button-delete"
    @click="deleteSign"
  >
    DELETE
  </button>
  <p class="result">{{ result }}</p>
</template>

<style>
.list {
  list-style: none;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

.list__button-name,
.list__button-delete {
  margin: 10px;
  background-color: green;
  height: 60px;
  border: none;
  border-radius: 20px;
  color: white;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
}

.list__button-name {
  font-size: 40px;
  width: 50px;
}

.list__button-delete {
  font-size: 20px;
  width: 100px;
}
</style>
