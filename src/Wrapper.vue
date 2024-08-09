<script setup>
import { defineProps } from 'vue';

defineProps({
    status: Object,
});
</script>

<template>
    <div id="wrapper">
        <h1>Wrapper text... {{ status.message }}</h1>
        <slot />
    </div>
</template>
