<script setup>
import { ref } from 'vue';

const count = ref(0);
let hovered = 0;

const increment = () => count.value++;
const decrement = () => count.value--;
const log = () => {
    hovered++;
    console.log(hovered);
};
</script>

<template>
    <div id="counter">
        <button @click="decrement">-</button>
        <span
            @mouseover="log"
            :style="{
                display: count >= 0 ? 'block' : 'none',
            }"
            >{{ count }}</span
        >
        <button @click="increment">+</button>
    </div>
</template>

<style scoped>
div {
    display: flex;
    gap: 0.5rem;
}

div > * {
    padding: 0.5rem;
}

button {
    border-radius: 0.5rem;
    border: none;
    outline: none;
    cursor: pointer;
}
</style>
