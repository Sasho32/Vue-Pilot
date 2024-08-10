<script setup>
// ako e podaden greshen type mai si raboti ama izkarva warning - demek e za dev lelev
// defaulta she izleze samo ako nyama podaden message gore!, dori i za e prazen ili "" primerno - si go ima i nyama nyjda ot defolt
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
