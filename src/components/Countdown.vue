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
justify-content: center;
}
.countdown-text {
text-align: left;
flex-wrap: nowrap;
}

.label {
  font-size: clamp(14px, 5vw, 45px);
}

#timer {
  font-size: clamp(14px, 8vw, 45px);
}
</style>
