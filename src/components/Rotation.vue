<template>
    <div class="rotation">
        <template v-for="(map, index) in frontlineALL" :key="index" >
            <div class="rotation-unit" :class="{ 'highlight': index === currentIndex }">{{ map }}</div>
            <span v-if="index < frontlineALL.length - 1" class="arrows">→</span>
        </template>        
    </div>

</template>

<script setup lang="ts">
import { ref } from 'vue';
import { frontlineALL, getMapIndex, getMap } from '../utils/getMap';

const today = new Date();
const currentIndex = ref(getMapIndex(today));
</script>

<style scoped>
.rotation {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 0.5rem;
    border-radius: 10px;
    background-color: var(--bg-card);
    padding:5px;
    flex-wrap: wrap;
}
.rotation span{
    margin: 0 -5px;
}
.rotation-unit {
  border-radius: 5px;
  white-space: nowrap;
  font-size: clamp(14px, 4.5vw, 40px);
  font-weight: 400 !important;
  /*background-color: rgb(221, 222, 221);*/
}
.arrows {
  font-size: clamp(14px, 3vw, 40px);
  font-weight: 400 !important;
}
.highlight {
    font-weight: bold !important;
    border-radius: 5px;
    border: 1px solid #529746;
    background-color: #83C87773;
    padding-inline: 5px;
}
</style>