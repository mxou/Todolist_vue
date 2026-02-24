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
    <p class="day-name">MARDI</p>
  </header>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=DM+Serif+Display&family=DM+Mono:wght@300;400&display=swap');

header {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding-bottom: 1.2rem;
  border-bottom: 1px solid #e0ddd8;
  margin-bottom: 2rem;
}

.number_date_container {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 10px;
}

.date {
  font-family: 'DM Serif Display', serif;
  font-size: 3.8rem;
  font-weight: 400;
  color: #dddddd;
  line-height: 1;
  margin: 0;
}

.text_date {
  display: flex;
  flex-direction: column;
  gap: 0;
}

.text_date p {
  font-family: 'DM Mono', monospace;
  font-size: 0.7rem;
  font-weight: 300;
  letter-spacing: 0.12em;
  color: #c4c2c2;
  margin: 0;
  line-height: 1.4;
}

.day-name {
  font-family: 'DM Mono', monospace;
  font-size: 0.65rem;
  font-weight: 300;
  letter-spacing: 0.2em;
  color: #c4c2c2;
  margin: 0;
}
</style>
