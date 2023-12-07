<template>
    <div id="player">
        <div :style="style" id="game">
            <Ground ref="ground"/>
            <Block v-if="curBlock" :init="curBlock"/>
        </div>
    </div>
</template>


<script setup lang="ts">
import Ground from '@/components/tetris/ground/Ground.component.vue';
import Block from '../block/Block.component.vue';
import { cellSize, height, width} from '@/components/tetris/common/history'

import { computed, ref } from 'vue';
import { onMounted } from 'vue';
import { nextTick } from 'vue';

const style = computed(() => ({
  width: cellSize*width+'px' ,
  height: cellSize*height+'px',
}));

const blockShapes = {
    L: [
        [[1, 1], [1, 0], [0, 0], [-1, 0]],
        [[1, -1], [0, -1], [0, 0], [0, 1]],
        [[-1, -1], [-1, 0], [0, 0], [1, 0]],
        [[-1, 1], [0, 1], [0, 0], [0, -1]]
    ]
}
const curBlock = ref(null);
const nextBlock = ref({});
let blockId = 0;

onMounted(() => {
    createNextBlock();
    next();
})


const createNextBlock = () => {
    let blockType = 'I'
    // A changer après avec des blocks randoms

    let shapes = blockShapes['L'];
    nextBlock.value = {
        shapes,
        pos : [0,0],
        class: blockType,
        id : blockId++
    }
}

const next = () => {
    curBlock.value = Object.assign({},nextBlock.value)
    curBlock.value.pos = [Math.floor(width/2)-1,height]
}


</script>


<style>
.game {
    position: relative;
    outline: solid 1px white;
    background-color: yellow;
    overflow: hidden;
}
</style>