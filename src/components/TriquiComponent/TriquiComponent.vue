<template>
    <div class="triqui-wrap">
        <div id="triqui-grid">
            <div class="cell" v-for="(cell, index) in grid" :key="index" :id="index"
                :style="{ cursor: (turn % 2 !== 0) ? xCursor : oCursor }" @click="cellIsEmpty(cell)">
                <img v-if="cell === 'x'" src="/assets/x.png" alt="">
                <img v-if="cell === 'o'" src="/assets/o.png" alt="">
            </div>
        </div>
    </div>
</template>
<script setup>
//import { ref } from 'vue'

import { ref } from "vue"
//import { onMounted } from "vue";
//import { h } from 'vue'


let xCursor = 'url(/assets/x-cursor.png) , pointer'
let oCursor = 'url(/assets/o-cursor.png) , pointer'
//let x = h('img', { src: '/assets/x.png' })
//let o = '<img src="/assets/o.png" />'

let grid = ref([1, 2, 3, 4, 5, 6, 7, 8, 9])

let turn = ref(1)

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

}
</script>

<style scoped>
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