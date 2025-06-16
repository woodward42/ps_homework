<script setup>
import { ref } from 'vue'
import AppHeader from './components/AppHeader.vue'
import GameCard from './components/GameCard.vue'

//переменная для хранения очков, которую передадим в BadgeScore
const currentScore = ref(0);

</script>

<template>
  <AppHeader />
  <hr />
  <div style="display: flex; justify-content: center">
    <GameCard
      @flip-card="console.log('flipped')"
      @set-card-status="(payload) => console.log(`card status changed: ${payload}`)"
    />
  </div>
</template>

<style scoped></style>
