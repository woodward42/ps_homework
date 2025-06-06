<script setup>
import Heart from './icons/Heart.vue'

const props = defineProps({
  score: Number,
})
</script>

<template>
  <div class="badge-score-container">
    <span class="score">{{ score }}</span>
    <Heart />
  </div>
</template>

<style scoped>
.badge-score-container {
  border-radius: 36px;
  background-color: #cce8ff;
  padding: 12px 24px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 10px;
}

.score {
  color: var(--button-color-primary-bg);
  font-weight: 700;
  font-size: 16px;
  line-height: 24px;
  text-align: center;
}
</style>
