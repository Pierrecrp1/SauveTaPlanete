<template>
  <span class="block">
    <!-- <cell v-for="cell of cells" :data="cell.data" :stage="stage" :pos="cell.pos" :key="cell.id"></cell> -->
    <cell v-for="cell of cells" :position="cell.pos" :key="cell.id"></cell>
</span>
</template>

<script setup lang="ts">
import Cell from '@/components/tetris/cell/cell.component.vue'
import { computed, ref } from 'vue';

interface initPos {
  pos : number[]
}

const props = defineProps({
  init : {
    type: Object,
    required:true
  }
})

const cellId = ref(0);
const idx = ref(0);
const x = ref(props.init.pos[0]);
const y = ref(props.init.pos[1]);
const fromCellId = ref(cellId.value);

const cells = computed(() => {
  return (props.init.shapes as [number, number][]).map(([cellX, cellY], index) => ({
    pos: [cellX + x.value, cellY + y.value],
    id: fromCellId.value + index,
  }));
});

</script>

<style>

</style>