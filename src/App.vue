<script setup>
//текущая дата
const curDate = new Date().toLocaleString("ru-RU");
</script>

<template>
  
  <!-- Дата на момент загрузки страницы  -->
  <div>Текущая дата: {{ curDate }}</div>
</template>

<style scoped></style>
