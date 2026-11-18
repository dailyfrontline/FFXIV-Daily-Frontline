<template>
    <div id="glance">{{ mapToday }}</div>

</template>

<script setup lang="ts">
import { getMap } from '../utils/getMap'
import { ref } from 'vue'
const mapToday = ref(getMap(new Date()))
</script>

<style scoped>
#glance {
    font-weight: bold;
}
</style>

