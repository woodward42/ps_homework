<script setup>
import WrongSmall from './icons/WrongSmall.vue'
import WrongBig from './icons/WrongBig.vue'
import RightSmall from './icons/RightSmall.vue'
import RightBig from './icons/RightBig.vue'



const props = defineProps({ cardState: Object, cardNumber: Number })
const emit = defineEmits(['flipCard', 'setCardStatus'])

//обработчик для переворота карты
function emitFlipCard() {
  emit('flipCard')
}

//обработчик для установки статуса
function emitSetCardStatus(status) {
  emit('setCardStatus', status)
}
//---
</script>

<template>
  <div class="game-card-container">
    <div class="game-card-inner-container">
      <span class="game-card-number-container">{{ cardNumber }}</span>
      <div
        v-if="cardState.status !== 'pending'"
        class="game-card-status-container"
      >
        <RightSmall v-if="cardState.status === 'right'" />
        <WrongSmall v-else />
      </div>
      <span
        v-if="cardState.state === 'closed'"
        class="word rus-word"
        >{{ cardState.translation }}</span
      >
      <span
        v-else
        class="word eng-word"
        >{{ cardState.word }}</span
      >

      <div class="game-card-action-container">
        <div
          v-if="cardState.state === 'closed'"
          @click="emitFlipCard"
          class="action-flip"
        >
          Перевернуть
        </div>

        <div
          v-else-if="cardState.state === 'opened' && cardState.status === 'pending'"
          class="action-right-wrong"
        >
          <WrongSmall @click="emitSetCardStatus('wrong')" />
          <RightSmall @click="emitSetCardStatus('right')" />
        </div>

        <div
          v-else
          class="action-done"
        >
          Завершено
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
  text-align: center;
}

.game-card-number-container {
  position: absolute;
  top: -9px;
  left: 20px;
  background-color: #ffffff;
}

.game-card-status-container {
  position: absolute;
  top: -9px;
  left: 110px;
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

.action-flip,
.action-done {
  font-weight: 700;
  font-size: 12px;
  text-transform: uppercase;
  letter-spacing: 0.12em;
}
.action-flip:hover {
  cursor: pointer;
}
</style>
