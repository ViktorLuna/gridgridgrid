<template>
    <div class="player">
      <h2>Player {{ player }}</h2>
      <GridComponent :gridData="myGrid" @cellClicked="handleCellClick" />
      <GridComponent :gridData="opponentGrid" />
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  import GridComponent from './GridComponent.vue';
  
  const props = defineProps({
    player: {
      type: Number,
      required: true,
    },
  });
  
  const myGrid = ref([]);
  const opponentGrid = ref([]);
  
  const handleCellClick = (cell) => {
    console.log(cell)
  };
  </script>