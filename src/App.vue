<template>
  <div class="container">
    <div class="player">
      <h2>Player 1</h2>
      <PlayerGrid :player="1" />
    </div>
    <div class="player">
      <h2>Player 2</h2>
      <PlayerGrid :player="2" />
    </div>
  </div>
</template>

<script setup>
import PlayerGrid from './components/GridComponent.vue';
</script>

<style scoped>
.container {
  display: flex;
  justify-content: space-between;
}

.player {
  width: 45%;
}
</style>