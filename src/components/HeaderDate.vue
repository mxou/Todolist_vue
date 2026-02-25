<script setup>
// defineProps({})
const current = new Date()
const date = `${current.getDate()}/${current.getMonth() + 1}/${current.getFullYear()}`

const day = current.getDate()
const month = current.getMonth() + 1
const year = current.getFullYear()
console.log(date)
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
  width: 40vw;
}

.number_date_container {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 10px;
}

.date {
  font-family: 'DM Serif Display', serif;
  font-size: 5rem;
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
  font-size: 1.1rem;
  font-weight: 300;
  letter-spacing: 0.12em;
  color: #c4c2c2;
  margin: 0;
  line-height: 1.4;
}

.day-name {
  font-family: 'DM Mono', monospace;
  font-size: 1.2rem;
  font-weight: 300;
  letter-spacing: 0.2em;
  color: #c4c2c2;
  margin: 0;
}
</style>
