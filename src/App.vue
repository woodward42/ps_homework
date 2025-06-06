<script setup>
import AppHeader from './components/AppHeader.vue'
import GameCard from './components/GameCard.vue'
</script>

<template>
  <AppHeader />
  <hr />
  <div style="display: flex; justify-content: center">
    <GameCard
      @flip-card="console.log('flipped')"
      @set-card-status="console.log(`card status changed`)"
    />
  </div>
</template>

<style scoped></style>
