<script setup>
import { defineProps } from 'vue';

defineProps({
    message: {
        type: Boolean,
        default: false,
    },
});
</script>

<template>
    <h1>{{ message }}</h1>
</template>

<style scoped>
h1 {
    background-color: bisque;
    padding: 1rem;
    text-align: center;
    color: #333;
    align-self: stretch;
}
</style>
