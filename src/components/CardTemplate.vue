<template>
  <div class="card">
    <slot />
  </div>
</template>

<style scoped>
.card {
    display: flex;
    text-align: center;
    align-items: center;
    justify-content: center;
    border:0;
    border-radius: 10px;
    background-color: var(--bg-card);
}
</style>
