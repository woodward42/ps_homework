<script setup></script>

<template>
  <button class="app-button">
    <slot>Начать игру</slot>
  </button>
</template>

<style scoped>
.app-button {
    width: 335px;
  padding: 16px 10px;
  border: transparent;
  border-radius: 100px;
  background-color: var(--button-color-primary-bg);
  color: var(--button-color-primary);
}

.app-button:hover {
  cursor: pointer;
}
</style>
