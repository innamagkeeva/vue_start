<script setup lang="ts">
import { ref } from 'vue'

const textInput = ref('')
const textInput2 = ref('')
const selectedGender = ref('')
</script>

<template>
  <div class="user">
    <input
      class="user__box"
      type="text"
      placeholder="Введите имя"
      v-model="textInput"
    />
    <input
      class="user__box"
      type="text"
      placeholder="Ведите фамилию"
      v-model="textInput2"
    />
    <div class="user__box">
      <select
        class="user__select"
        name="floor"
        v-model="selectedGender"
      >
        <option value="">-- Выберите пол --</option>
        <option value="male">мужской</option>
        <option value="female">женский</option>
      </select>
    </div>
    <button
      class="user__box user__button-show"
      type="button"
      @click="console.log('меня нажали')"
      :disabled="textInput.length === 0 || textInput2.length === 0 || selectedGender.length === 0"
    >
      Показать
    </button>
  </div>

  <div class="letter">
    <ul class="double">
      <li class="double__li">
        {{ textInput }}
      </li>
      <li class="double__li">
        {{ textInput2 }}
      </li>
      <li class="double__li double__li-3">{{ selectedGender }}</li>
    </ul>
  </div>
</template>

<style>
.user {
  display: flex;
  flex-direction: column;
}

.double {
  margin: 0;
  padding: 0;
}

.user,
.letter {
  height: 300px;
  width: 350px;
  margin: 0 auto;
}

.user__box {
  border: 1px solid black;
  border-radius: 15px;
}
.user__box,
.double__li {
  height: 40px;
  margin-bottom: 20px;
  cursor: pointer;
  font-size: 20px;
  padding: 0 10px;
  outline: none;
}

.user__select {
  width: 100%;
  height: 30px;
  font-size: 20px;
  border: none;
  outline: none;
  cursor: pointer;
}

.user__button-show {
  background-color: green;
}

.double {
  list-style: none;
}
</style>

<!-- не понимаю как сделать чтоб вначале в инпуте был только placeholder, а при вводе - внизу в дубле шел сначала текст ("Ваше имя  или Ваша фамилия" и вводимые буквы) -->

<!-- почему на кнопке задизейбливается только слово "показать", а не вся кнопка.  
 И! почему срабатывает со знаком ||  а не &&     -->

<!-- а как открыть нижнее поле после нажатия "Показать" = вообще не догоняю... -->
