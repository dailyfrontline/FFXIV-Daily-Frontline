<template>
  <div class="countdown">
    <div class="countdown-text">
      <div class="label">下次轮换：</div>
      <span id="timer">{{ timeLeft }}</span>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed} from 'vue';
import { formatTimeDiff } from '../utils/formatTimeDiff';
import { getCountdown } from '../utils/getCountdown';
const timeNow = ref(new Date());
setInterval(() => {
  timeNow.value = new Date();
}, 1000);

const timeLeft = computed(() => {
  const countdown = getCountdown(timeNow.value);
  return formatTimeDiff(countdown);
});

</script>

<style scoped>
.countdown {
display: flex;
justify-content: flex-start;
outline: 1px solid red;
width: 100%;
}
.countdown-text {
text-align: center;
flex-wrap: nowrap;
width: 90%;
margin-left: 5%;
outline: 1px solid blue;

}

.label {
  font-size: clamp(14px, 6vw, 45px);
  font-weight: 500 !important;
}

#timer {
  font-size: clamp(14px, 8vw, 45px);
  font-weight: bold;
  font-variant-numeric: tabular-nums !important;
  color:blue;
}
</style>
