<template>
  <div class="countdown">
    <div class="countdown-text">
      <div class="label">下次轮换：</div>
      <span id="timer">{{ timeLeft }}</span>
      <span class="label"> 后</span>
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
justify-content: center;
}
.countdown-text {
text-align: left;
flex-wrap: nowrap;
}

.label {
font-size: 20px;
}

#timer {
  font-size: 35px;
}
</style>
