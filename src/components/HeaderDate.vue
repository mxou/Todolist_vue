<script setup>
defineProps({})
</script>

<template>
  <header>
    <div class="number_date_container">
      <h1 class="date">12</h1>
      <div class="text_date">
        <p>JAN</p>
        <p>2026</p>
      </div>
    </div>
    <p>MARDI</p>
  </header>
</template>

<style scoped>
header {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}
.number_date_container {
  /* border: 2px solid black; */
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 5px;
}

.date {
  font-size: 3rem;
}
</style>
