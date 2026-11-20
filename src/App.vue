<script setup lang="ts">
import TheCalendar from './components/TheCalendar.vue'
import Countdown from './components/Countdown.vue'
import Rotation from './components/Rotation.vue'
import QuickGlance from './components/QuickGlance.vue'

</script>

<template>
    <div class="container">
        <div class="container1">
          <div class="left1"><QuickGlance /></div>
          <div class="right1"><Countdown /></div>      
        </div>
        <div class="container2"><Rotation /></div>
        <div class="container3"><TheCalendar /></div>
    </div>



</template>

<style scoped>

.container {
  display: flex;
  flex-direction: column;
  gap: 8px;
  padding-inline: 24px;
  padding-block: 16px;

}

.container1 {
  /*display: flex;*/
  display: grid;
  grid-template-columns: 2fr 2fr;
  align-items: stretch;
  gap: 8px;
  min-width: 0;
}

.left1, .right1 {

  border-radius: 10px;
  background-color: var(--bg-card);
  flex: 1;
  text-align: center;
  min-height: 120px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.left1 {
  min-width: 0;
  font-size: 50px;
}

@media (max-width: 600px){
  .left1 {
    font-size: clamp(14px, 12vw, 50px);
  }
  #app {
    padding: 0 2rem;
  }
}



</style>
