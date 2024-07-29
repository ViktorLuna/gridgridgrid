<template>
  <div class="grid" :style="{ gridTemplateColumns: `repeat(${columns}, 1fr)` }">
    <div
      v-for="(row, rowIndex) in rows"
      :key="rowIndex"
      class="row"
      :style="{ gridTemplateRows: `repeat(${rows}, 1fr)` }"
    >
      <div
        v-for="(col, colIndex) in columns"
        :key="colIndex"
        class="cell"
        :class="{ selected: isSelected(rowIndex, colIndex) }"
        @click="toggleSelection(rowIndex, colIndex)"
      ></div>
    </div>
  </div>
  <button @click="seePositions()">seePositions</button>
</template>

<script setup>
import { computed, ref } from 'vue';
import { defineComponent } from 'vue';

const props = defineProps({
  player: {
    type: Number,
    required: true,
  },
});

const rows = ref(10);
const columns = ref(10);
const selectedCells = ref([]);

const isSelected = (rowIndex, colIndex) => {
  return selectedCells.value.some(cell => cell.row === rowIndex && cell.col === colIndex);
};

const toggleSelection = (rowIndex, colIndex) => {
  const index = selectedCells.value.findIndex(cell => cell.row === rowIndex && cell.col === colIndex);
  if (index !== -1) {
    selectedCells.value.splice(index, 1);
  } else {
    selectedCells.value.push({ row: rowIndex, col: colIndex });
  }
};

const seePositions = () => {
  console.log('Player', props.player)

  for (const cell of selectedCells.value) {
    console.log(cell.row, cell.col);
  }
};
</script>

<style scoped>
.grid {
  display: grid;
  width: 400px;
  height: 400px;
  border: 1px solid black;
}

.row {
  display: grid;
}

.cell {
  border: 1px solid lightgray;
}

.selected {
  background-color: lightblue; /* Adjust the color as needed */
}
</style>