<!-- <script setup lang="ts">
import { ref, computed } from 'vue'

type GenderBase = {
  value: GenderSeparationValue
  text: string
}

type GenderSeparationValue = '' | 'male' | 'female'

const genders = ref<GenderBase[]>([
  { value: '', text: '---Выберите пол---' },
  { value: 'male', text: 'мужской' },
  { value: 'female', text: 'женский' },
])

const textInputName = ref('')
const textInputSurname = ref('')
const selectedGender = ref<GenderSeparationValue>('')
const isShowed = ref(false)

// function onSubmit(): void {
//   // Используем if для переключения состояния
//   if (isShowed.value) {
//     isShowed.value = false // Если данные показываются, скрываем их
//   } else {
//     isShowed.value = true // Если данные скрыты, показываем их
//   }
// }    //А упрощенная запись этой функции ниже :

function onSubmit(): void {
  isShowed.value = !isShowed.value
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
  opacity: 70%;
  cursor: not-allowed;
}
</style> -->

<script setup lang="ts">
import { computed, ref } from 'vue'

type CurrenciesSeparationValue = 'dollar-ruble' | 'ruble-dollar' | 'Euro-ruble' | 'ruble-Euro'

type CurrenciesBase = {
  value: CurrenciesSeparationValue
  text: string
  factor: number
}

const currencies = ref<CurrenciesBase[]>([
  { value: 'dollar-ruble', text: 'Доллар=>Рубль', factor: 100 },
  { value: 'ruble-dollar', text: 'Рубль=>Доллар', factor: 10 },
  { value: 'Euro-ruble', text: 'Евро=>Рубль', factor: 90 },
  { value: 'ruble-Euro', text: 'Рубль=>Евро', factor: 9 },
])

const selectedCurrency = ref<CurrenciesBase>(currencies.value[0])

const textInputDesired = ref(0)

const calc = computed(() => textInputDesired.value * selectedCurrency.value.factor)
</script>

<template>
  <div class="conversion">
    <label class="conversion__label">
      <input
        class="conversion__input window"
        type="number"
        v-model="textInputDesired"
      />
    </label>
    <select
      class="conversion__select window"
      name="currency"
      v-model="selectedCurrency"
    >
      <option
        v-for="currency in currencies"
        :key="currency.value"
        :value="currency"
      >
        {{ currency.text }}
      </option>
    </select>
    <span class="conversion__span window"> {{ calc }}</span>
  </div>
</template>

<style>
.conversion {
  width: 400px;
  height: 400px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  margin-top: 100px;
  padding: 20px;
  border: 2px solid black;
  border-radius: 5px;
}

.window {
  height: 40px;
  margin-bottom: 20px;
}

.conversion__input {
  border: none;
  outline: 0;
}

.conversion__select {
  border: 1px solid black;
  border-radius: 10px;
}
</style>
