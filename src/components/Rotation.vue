<template>
    <div class="rotation">
        <template v-for="(map, index) in frontlineALL" :key="index" >
            <div class="rotation-unit" :class="{ 'highlight': index === currentIndex }">{{ map }}</div>
            <span v-if="index < frontlineALL.length - 1">→</span>
        </template>        
    </div>

</template>

<script setup lang="ts">
import { ref } from 'vue';
import { frontlineALL, getMapIndex, getMap } from '../utils/getMap';

const today = new Date();
//console.log(today)
//console.log(getMap(today))
//console.log(getMapIndex(today))
alert(window.innerWidth);
const currentIndex = ref(getMapIndex(today));
</script>

<style scoped>
.highlight {
    font-weight: bold;
    border-radius: 5px;
    border: 1px solid black;
    padding-inline: 5px;
}
.rotation {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 0.5rem;
    border-radius: 5px;
    background-color: white;
    padding:5px;
    flex-wrap: wrap;
}
.rotation-unit {
  border-radius: 5px;
  white-space: nowrap;
  /*background-color: rgb(221, 222, 221);*/
}
</style>