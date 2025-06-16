<script setup>
import { ref } from 'vue'

import AppHeader from './components/AppHeader.vue'
import GameCard from './components/GameCard.vue'

//переменная для хранения очков, которую передадим в BadgeScore
const currentScore = ref(42)

//переменная для хранения карточек
const cardState = ref([
  {
    word: 'игра',
    translation: 'game',
    state: 'closed',
    status: 'pending',
  },
])
</script>

<template>
  <AppHeader :score="currentScore" />
  <hr />
  <div style="display: flex; justify-content: center">
    <GameCard
      :card-state="cardState[0]"
      @flip-card="console.log('flipped')"
      @set-card-status="(payload) => console.log(`card status changed: ${payload}`)"
    />
  </div>
</template>

<style scoped></style>
