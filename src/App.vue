<script setup>
import { ref } from 'vue'

import AppHeader from './components/AppHeader.vue'
import GameCard from './components/GameCard.vue'

//переменная для хранения очков, которую передадим в BadgeScore
const currentScore = ref(42)

//переменная для хранения карточек
const cards = ref([
  {
    word: 'game',
    translation: 'игра',
    state: 'closed',
    status: 'pending',
  },
  {
    word: 'game',
    translation: 'игра',
    state: 'opened',
    status: 'pending',
  },
  {
    word: 'game',
    translation: 'игра',
    state: 'opened',
    status: 'success',
  },
  {
    word: 'game',
    translation: 'игра',
    state: 'opened',
    status: 'error',
  },
])
</script>

<template>
  <AppHeader :score="currentScore" />
  <hr />
  <div style="display: flex; justify-content: center">
    <GameCard
      v-for="(card, idx) in cards"
      :key="`card-${idx}`"
      :card-state="card"
      @flip-card="console.log('flipped')"
      @set-card-status="(payload) => console.log(`card status changed: ${payload}`)"
    />
  </div>
</template>

<style scoped></style>
