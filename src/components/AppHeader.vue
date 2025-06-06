<script setup>
import BadgeScore from './BadgeScore.vue'
</script>

<template>
  <div class="header-container">
    <div class="header-logo">Запомни слово</div>
    <BadgeScore :score="101" />
  </div>
</template>

<style scoped>
.header-container {
  min-height: 100px;
  padding: 0 40px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.header-logo {
  font-weight: 700;
  font-size: 16px;
  letter-spacing: 0.12em;
  line-height: 24px;
  text-transform: uppercase;
}
</style>
