<script setup>
import WrongSmall from './icons/WrongSmall.vue'
import RightSmall from './icons/RightSmall.vue'

const emit = defineEmits(['flipCard', 'setCardStatus'])

//обработчик для переворота карты
function handleFlipCard() {
  console.log('handleFlepCard() call')
  emit('flipCard')
}

//обработчик для установки статуса
function handleSetCardStatus(status) {
  console.log('handlesetCardStatus() call')
  emit('setCardStatus', status)
}
</script>

<template>
  <div class="game-card-container">
    <div class="game-card-inner-container">
      <span class="game-card-number-container">42</span>
      <span class="word eng-word">ENG WORD</span>
      <span class="word rus-word">RUS WORD</span>
      <div class="game-card-action-container">
        <div
          @click="handleFlipCard"
          class="action-flip"
        >
          Перевернуть
        </div>
        <div class="action-right-wrong">
          <WrongSmall @click="handleSetCardStatus('wrong')" />
          <RightSmall @click="handleSetCardStatus('right')" />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.game-card-container {
  background-color: #ffffff;
  width: 250px;
  height: 376px;
  padding: 19px;
  border-radius: 16px;

  box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
}

.game-card-inner-container {
  position: relative;
  width: 100%;
  height: 100%;
  border: 1px solid #cce8ff;
  border-radius: 12px;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.word {
  font-weight: 400;
  font-size: 18px;
  align-self: center;
}

.game-card-number-container {
  position: absolute;
  top: -9px;
  left: 20px;
  font-size: 14px;
  background-color: #ffffff;
}

.game-card-action-container {
  min-width: 97px;
  position: absolute;
  bottom: -9px;
  left: 75px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #ffffff;
  padding: 0 4px;
}

.action-right-wrong {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
}

.action-flip {
  font-weight: 700;
  font-size: 12px;
  text-transform: uppercase;
  letter-spacing: 0.12em;
}
.action-flip:hover {
  cursor: pointer;
}
</style>
