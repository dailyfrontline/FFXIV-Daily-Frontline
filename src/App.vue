<script setup lang="ts">
import TheCalendar from './components/TheCalendar.vue'
import Countdown from './components/Countdown.vue'
import Rotation from './components/Rotation.vue'
import QuickGlance from './components/QuickGlance.vue'
import CardTemplate from './components/CardTemplate.vue';
</script>

<template>
    <div class="container">
        <div class="container1">
          <CardTemplate><QuickGlance id="glance-block"/></CardTemplate>
          <CardTemplate><Countdown id="countdown-block"/></CardTemplate>          
          <!--<div class="left1"><QuickGlance /></div>
          <div class="right1"><Countdown /></div> -->     
        </div>
        <div class="container2"><CardTemplate><Rotation id="rotation-block"/></CardTemplate></div>
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
#rotation-block {
padding-block: 8px;
}
#glance-block, #countdown-block {
  display: flex;
  align-items: center;
  min-height: 120px;
}

#glance-block {
  min-width: 0;
  font-size: 50px;
  font-weight: bold;

}

@media (max-width: 600px){
  #glance-block {
    font-size: clamp(14px, 12vw, 50px);
  }

}



</style>
