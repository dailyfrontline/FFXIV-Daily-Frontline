<script setup lang="ts">
import { getMap } from '../utils/getMap'
import { ref } from 'vue'


const attrs = ref([
  {
    key: 'today',
    highlight: {
      fillMode: 'light',

      style:{
        borderRadius:'10%',
        backgroundColor: '#83C87773',
        border: '1px solid #529746',        
        width:'100%',
        height:'100%',
        //boxShadow:'0 2px 4px #ccc',
        //opacity:'0.8'
        
      }
      
    },
    dates: new Date(),
    customData: {
      //mapToday: getMap(day.date),
    },
  },
])

const calendar = ref<any>(null);

const goToday = () => {
  calendar.value?.focusDate(new Date());
}
</script>


<template> 

    <VCalendar expanded borderless :attributes="attrs" ref="calendar" timezone="Asia/Shanghai" id="calendar">
      <template #day-content="{ day }">
        <div class="day-cell">
          <div class="day-number">{{ day.day }}</div>
          <div class="map-today">    {{ console.log(day.date) }}
      {{ console.log(getMap(day.date)) }}{{ getMap(day.date) }}</div> 
        </div>
      </template>
    </VCalendar>
  

  <div class="wrapper">
    <div @click="goToday">>&nbsp;跳转今天</div>
    <div>>&nbsp;订阅当月（*功能开发中）</div>
  </div>     
</template>


<style>
.wrapper {
  /*display: flex;
  justify-content: flex-start;*/
  font-size: clamp(8px, 4vw, 30px);
}
#calendar {
  border-radius: 10px;
}
.day-cell {
  text-align: center;
  min-height: 0px;
  height: auto;
  /*background-color:rgba(131, 200, 119, 0.452);/*为了调试的时候看着方便*/
  justify-content: center;
  align-items: center;
  margin-bottom: 3px;

}
.day-number {
  font-size: clamp(8px, 4vw, 25px);
}
.map-today {
  font-size: clamp(8px, 3.5vw, 25px);
}
</style>