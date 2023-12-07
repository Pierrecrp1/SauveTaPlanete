<template>
    <div class="cell" :style="style"></div>
</template>


<script setup lang="ts">
import { computed } from 'vue';
import { cellSize, height, width} from '@/components/tetris/common/history'

const props = defineProps({
    position: {
        type: Array,
        required: true
    }
})


const style = computed(() => ({
  width: cellSize + 'px',
  height: cellSize + 'px',
  left: parseInt(props.position[0]) * cellSize + 'px',
  bottom: parseInt(props.position[1]) * cellSize + 'px',
}));
</script>


<style scoped>
.cell {
    position: absolute;
    background-color: white;
}
</style>