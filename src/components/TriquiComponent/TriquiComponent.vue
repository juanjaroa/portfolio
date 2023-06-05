<template>
    <div class="section">
        <header>
            <div>
                <img :src="assetX" alt="">
                <p>{{ wonX }}</p>
            </div>
            <div>
                <img :src="assetO" alt="">
                <p>{{ wonO }}</p>
            </div>
        </header>
        <div class="triqui-wrap">
            <div id="triqui-grid">
                <div class="cell" v-for="(cell, index) in grid" :key="index" :id="index"
                    :style="{ cursor: (turn % 2 !== 0) ? xCursor : oCursor }" @click="cellIsEmpty(cell)">
                    <img v-show="cell === 'x'" :src="assetX" alt="">
                    <img v-show="cell === 'o'" :src="assetO" alt="">
                </div>
            </div>
        </div>
        <ModalDialog :winner="winner" @modalClosed="handleModalClosed" />
    </div>
</template>
<script setup>
import { ref } from "vue"
import ModalDialog from '../ModalDialog.vue'

let assetX = '/assets/x.png'
let assetO = '/assets/o.png'

let xCursor = 'url(/assets/x-cursor.png) , pointer'
let oCursor = 'url(/assets/o-cursor.png) , pointer'

let grid = ref([1, 2, 3, 4, 5, 6, 7, 8, 9])
let turn = ref(1)
let winner = ref()
let wonX = ref(0)
let wonO = ref(0)

function resetTrique() {
    grid.value = [1, 2, 3, 4, 5, 6, 7, 8, 9]
    turn.value = 1
    winner = ref()
}

//Funcion para manejar el evento
const handleModalClosed = () => {
    if (winner.value === 'x') {
        wonX.value++
    } else if (winner.value === 'o') {
        wonO.value++
    }
    resetTrique()
}

function cellIsEmpty(cell) {
    typeof (cell) === 'number' ? playTriqui(cell) : ''
}

function playTriqui(cell) {
    if (turn.value % 2 !== 0) {
        grid.value[grid.value.indexOf(cell)] = 'x'
        turn.value++
    } else {
        grid.value[grid.value.indexOf(cell)] = 'o'
        turn.value++
    }

    if (turn.value >= 5) {
        winner.value = checkWinner()
    }
}

const checkWinner = () => {
    const winningCombinations = [
        [0, 1, 2], // filas
        [3, 4, 5],
        [6, 7, 8],
        [0, 3, 6], // columnas
        [1, 4, 7],
        [2, 5, 8],
        [0, 4, 8], // diagonales
        [2, 4, 6]
    ];

    for (const combination of winningCombinations) {
        const [a, b, c] = combination;
        if (grid.value[a] === grid.value[b] && grid.value[a] === grid.value[c]) {
            return grid.value[a]
        }
    }
    return;
};

</script>

<style scoped>
.section {
    width: 50%;
    max-width: 500px;
    display: flex;
    flex-direction: column;
    gap: 2rem;
    align-items: center;
}

header,
header>div {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 1rem;
    font-size: 1.5rem;
}

header {
    width: 100%;
}

header img {
    height: 1.5rem;
}

.triqui-wrap {
    overflow: hidden;
}

#triqui-grid {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    scale: 1.1;
}

.cell {
    width: 5rem;
    aspect-ratio: 1/1;
    font-family: Roboto-Black;
    border: 5px solid;
    display: flex;
    justify-content: center;
    align-items: center;
    line-height: 1em;
    font-size: 3rem;
}

.cell img {
    width: 66%;
}
</style>