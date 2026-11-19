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
        backgroundColor: 'var(--highlight)',
        border: '1px solid var(--highlight-border)',        
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
          <div class="day-number" :class="{ 'is-today': day.isToday }">{{ day.day }}</div>
          <div class="map-today" :class="{ 'is-today': day.isToday }">{{ getMap(day.date) }}</div> 
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
  background-color: var(--bg-card);
}
.day-cell {
  text-align: center;
  min-height: 0px;
  height: auto;
  /*background-color:rgba(131, 200, 119, 0.452);/*为了调试的时候看着方便*/
  justify-content: center;
  align-items: center;
  margin-bottom: 3px;
  color: var(--text-primary);
}
.day-number {
  font-size: clamp(8px, 4vw, 25px);
}
.map-today {
  font-size: clamp(8px, 3.5vw, 25px);
}
.is-today {
  font-weight: bold;
}
.vc-title {
  background-color: #f1f1f1;/*var(--bg-primary) */
  font-size: clamp(15px, 3vw, 25px);
}
.vc-arrow {
  background-color: #f1f1f1;
  /*width: clamp(5px, 2.5vw, 35px);
  height: auto;
  aspect-ratio: 1/1;*/
}
/*.vc-header {
  grid-template-rows: auto;
  height: auto;
  min-height: max-content;  
}*/

@media (prefers-color-scheme: dark) {
.vc-title {
  background-color: var(--bg-primary);/*var(--bg-primary) 505b52*/
  color: #dbdbdb !important;
}
.vc-arrow {
  background-color: var(--bg-primary);/*dbdbdb*/
  color: #dbdbdb !important;
}  

}

</style>