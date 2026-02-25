<script setup>
const current = new Date()
const day = current.getDate()
const month = current.getMonth() + 1
const year = current.getFullYear()

const dayNames = ['DIMANCHE', 'LUNDI', 'MARDI', 'MERCREDI', 'JEUDI', 'VENDREDI', 'SAMEDI']
const dayName = dayNames[current.getDay()]
</script>

<template>
  <header>
    <div class="number_date_container">
      <h1 class="date">{{ day }}</h1>
      <div class="text_date">
        <p>{{ month }}</p>
        <p>{{ year }}</p>
      </div>
    </div>
    <p class="day-name">{{ dayName }}</p>
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
  border-bottom: 1px solid #e0ddd827;
  margin-bottom: 2rem;
  width: 100%;
}

.number_date_container {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 10px;
}

.date {
  font-family: 'DM Serif Display', serif;
  font-size: clamp(3rem, 8vw, 5rem);
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
  font-size: clamp(0.75rem, 2.5vw, 1.1rem);
  font-weight: 300;
  letter-spacing: 0.12em;
  color: #c4c2c2;
  margin: 0;
  line-height: 1.4;
}

.day-name {
  font-family: 'DM Mono', monospace;
  font-size: clamp(0.65rem, 2.5vw, 1.2rem);
  font-weight: 300;
  letter-spacing: 0.2em;
  color: #c4c2c2;
  margin: 0;
}
</style>
