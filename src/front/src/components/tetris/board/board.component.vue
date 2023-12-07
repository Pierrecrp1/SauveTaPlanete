<template>
    <div class="board" style="">
      <Player/>
    </div>
</template>


<script setup lang="ts">
import Player from '@/components/tetris/player/Player.component.vue'
import { computed } from 'vue';

const currentPieceIndex = 0

const generateEmptyBoard = () => {
  return Array.from({ length: 22 }, () => Array(10).fill(0));
}



const board = generateEmptyBoard();

</script>

<style>
.board {
    position: relative;
    border: 1px solid #ccc;
    width: fit-content; /* Pour occuper la largeur totale du parent */
    height: fit-content;

}
</style>