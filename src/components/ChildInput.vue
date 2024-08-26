<script setup>
const props = defineProps({
    name: String,
    inputHandler: Function,
});
</script>

<template>
    <input
        type="text"
        :value="name"
        @input="inputHandler($event.target.value)"
    />
</template>

<style scoped></style>
