<template>
    <div class="tetris">
        <player :stage="stage" :keys="{ straight: 32, left: 37, rotate: 38, right: 39, down: 40 }" ref="player" />
    </div>
</template>

<script>
import player from './player.vue'
import stageComputed from './stageComputed'

export default {
    name: 'tetris',
    mixins: [stageComputed],
    data() {
        return {
            stage: {
                cellSize: 30,
                width: 10,
                height: 22,
                blockType: {
                    I: {
                        forme: [
                            [1, 1, 1, 1],
                            [0, 0, 0, 0],
                            [0, 0, 0, 0],
                            [0, 0, 0, 0],
                        ],
                        color: "#4DD0E1",
                        pos: [0, 3],
                    },
                    O: {
                        forme: [
                            [1, 1, 0, 0],
                            [1, 1, 0, 0],
                            [0, 0, 0, 0],
                            [0, 0, 0, 0],
                        ],
                        color: "#FFEB3B",
                        pos: [0, 4],
                    },
                    T: {
                        forme: [
                            [0, 1, 0, 0],
                            [1, 1, 1, 0],
                            [0, 0, 0, 0],
                            [0, 0, 0, 0],
                        ],
                        color: "#AB47BC",
                        pos: [0, 2],
                    },
                    S: {
                        forme: [
                            [1, 1, 0, 0],
                            [0, 1, 1, 0],
                            [0, 0, 0, 0],
                            [0, 0, 0, 0],
                        ],
                        color: "#4CAF50"
                    },
                    Z: {
                        forme: [
                            [0, 1, 1, 0],
                            [1, 1, 0, 0],
                            [0, 0, 0, 0],
                            [0, 0, 0, 0],
                        ],
                        color: "#E53935"
                    },
                    J: {
                        forme: [
                            [0, 0, 1, 0],
                            [1, 1, 1, 0],
                            [0, 0, 0, 0],
                            [0, 0, 0, 0],
                        ],
                        color: "#283593"
                    },
                    L: {
                        forme: [
                            [1, 0, 0, 0],
                            [1, 1, 1, 0],
                            [0, 0, 0, 0],
                            [0, 0, 0, 0],
                        ],
                        color: "#F57C00",
                        pos: [0, 4],
                    }
                },
                blocks: ['I', 'O', 'T', 'S', 'Z', 'J', 'L']
            }
        }
    },
    components: { player }
}
</script>

