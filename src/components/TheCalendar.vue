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

.vc-title {
  background-color: #f1f1f1;/*var(--bg-primary) */
  color: #141c15 !important;/*？不知道为什么title和arrow的颜色表现很奇怪 但是算了先不管了*/
}
.vc-arrow {
  background-color: #f1f1f1;
  color: #364538 !important;
}

@media (prefers-color-scheme: dark) {
.vc-title {
  background-color: #e2ede5;/*var(--bg-primary) 505b52*/
}
.vc-arrow {
  background-color: #e2ede5;/*dbdbdb*/
}  

}

</style>