<script setup>
import { ref } from 'vue';
import ChildInput from './ChildInput.vue';

const name = ref('Some name');
</script>

<template>
    <input type="text" :value="name" @input="name = $event.target.value" />
    <ChildInput :value="name" :inputHandler="newName => (name = newName)" />
</template>

<style scoped></style>
