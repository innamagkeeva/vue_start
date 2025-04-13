<script setup lang="ts">
import { ref } from 'vue'
import { computed } from 'vue'

type GenderBase = {
  value: string
  text: string
}

const genders: GenderBase[] = ref([
  { value: '', text: '---Выберите пол---' },
  { value: 'male', text: 'мужской' },
  { value: 'female', text: 'женский' },
])

const textInputName = ref('')
const textInputSurname = ref('')
const selectedGender = ref('')
const isShowed = ref(false)

// const buttonText = ref('показать')

// function onSubmit(): void {
//   isShowed.value = true
//   buttonText.value = 'скрыть'
// }

function onSubmit(): void {
  // Используем if для переключения состояния
  if (isShowed.value) {
    isShowed.value = false // Если данные показываются, скрываем их
  } else {
    isShowed.value = true // Если данные скрыты, показываем их
  }
}

const buttonText = computed(() => (isShowed.value ? 'скрыть' : 'показать')) // Условный текст кнопки
</script>

<template>
  <form
    class="form"
    @submit.prevent="onSubmit"
  >
    <input
      class="form__box"
      type="text"
      placeholder="Введите имя"
      v-model="textInputName"
    />
    <input
      class="form__box"
      type="text"
      placeholder="Ведите фамилию"
      v-model="textInputSurname"
    />
    <div class="form__box">
      <select
        class="form__select"
        name="gender"
        v-model="selectedGender"
      >
        <option
          v-for="gender in genders"
          :key="gender.value"
          :value="gender.value"
        >
          {{ gender.text }}
        </option>
      </select>
    </div>
    <button
      class="form__box form__button-show"
      type="submit"
      :disabled="
        textInputName.length === 0 || textInputSurname.length === 0 || selectedGender.length === 0
      "
    >
      {{ buttonText }}
    </button>
  </form>

  <div
    class="user-data"
    v-if="isShowed"
  >
    <ul class="list">
      <li class="list__li">Ваше имя: {{ textInputName }}</li>
      <li class="list__li">Ваша фамилия: {{ textInputSurname }}</li>
      <li class="list__li">Ваш пол: {{ selectedGender }}</li>
    </ul>
  </div>
</template>

<style>
.form {
  display: flex;
  flex-direction: column;
}

.list {
  margin: 0;
  padding: 0;
  list-style: none;
}

.form,
.user-data {
  height: 300px;
  width: 350px;
  margin: 0 auto;
}

.form__box {
  border: 1px solid black;
  border-radius: 15px;
}
.form__box,
.list__li {
  height: 40px;
  margin-bottom: 20px;
  cursor: pointer;
  font-size: 20px;
  padding: 0 10px;
  outline: none;
}

.form__select {
  width: 100%;
  height: 30px;
  font-size: 20px;
  border: none;
  outline: none;
  cursor: pointer;
}

.form__button-show {
  background-color: green;
}

.form__button-show:disabled {
  opacity: 50%;
  cursor: not-allowed;
}
</style>

<!-- вопросы:
 1)  { value: 'male', text: 'мужской' } какую задачу имеет value: 'male' если пользователю видно только значение 'мужской'?
 ПРАВИЛЬНО ЛИ Я ПОНИМАЮ  что это только ключ и нужен только для  работы с кодом? -->

<!-- 2)в опциях: почему в поле по умолчанию выводится строка именно с пустой строкой в value? я пробовала менять местами в коде - все равно она, значит не по порядку, а именно с пустой строкой (---Выберете пол---) -->

<!-- 3)
 как при нажатии на "показать" открывать нижнее поле и менять текст на "скрыть" я быстро сама поняла, а вот обратно - вообще не придумала, хотя пыталась долго.  то что написала - взяла из GPT?, к стати несколько разных готовых вариантов посмотрела.   каждая строчка понятна, а в целом не очень складывается в голове.. надо чтоб словами ты рассказал.     ну или вариант правильнее -->
