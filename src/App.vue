<script setup>
import { ref, onMounted } from 'vue'

import AppHeader from './components/AppHeader.vue'
import GameCard from './components/GameCard.vue'
import AppButton from './components/AppButton.vue'

//переменная для хранения очков, которую передадим в BadgeScore
let currentScore = ref(42)

//переменная для хранения карточек
const cards = ref([])

//api ссылка
const API_WORDS_URL = 'http://localhost:8080/api/random-words'

//функция получения данных по апи
async function getWords() {
  try {
    const response = await fetch(API_WORDS_URL)

    //массив до обработки
    let cardsRaw = await response.json()

    cards.value = cardsRaw.map((card) => ({ ...card, state: 'closed', status: 'pending' }))
  } catch (e) {
    // обработка ошибок
  }
}

//function handleFlipCard
function handleFlipCard(idx) {
  cards.value[idx].state = 'opened'
}

//function handleSetCardStatus
function handleSetCardStatus(idx, status) {
  cards.value[idx].status = status

  if (status === 'right'){
    currentScore.value+=10
  }
  else{
    currentScore.value-=4
  }
}

//начать заново
function resetGame(){
  currentScore.value = 42;
  getWords()
}

onMounted(() => {
  getWords()
})
</script>

<template>
  <AppHeader :score="currentScore" />
  <hr />
  <template v-if="cards.length">
    <div class="cards-container">
      <GameCard
        v-for="(card, idx) in cards"
        :key="`card-${idx}`"
        :card-state="card"
        :card-number="idx"
        @flip-card="handleFlipCard(idx)"
        @set-card-status="(status) => handleSetCardStatus(idx, status)"
      />
    </div>
    <hr />
    <div style="display: flex; justify-content: center;"><AppButton @click="resetGame">Начать заново</AppButton></div>
  </template>
</template>

<style scoped>
.cards-container {
  width: 80%;
  display: flex;
  justify-content: center;
  gap: 10px;
  flex-wrap: wrap;
  margin: auto;
}
</style>
