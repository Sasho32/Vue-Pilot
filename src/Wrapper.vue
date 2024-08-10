<script setup>
defineProps({
    status: Object,
});
</script>

<template>
    <div id="wrapper">
        <h1>Wrapper text... {{ status.message }}</h1>
        <slot />
        <!-- kato {children, moje i samozatvaryasht se tag}, i bez tva ako slojim neshto mejdy otv i zatv slot she go zameni s realnoto dete/deca -->
    </div>
</template>

<!-- DOLNOTO NIKYDE NE SYM GO SLOJIL I PROSTO TOYA COMPONENT E NAI MALYK I TYK OBYASNYAVAM -->
<!-- 

za da ne pravim tova: 

    <input
    :value="text"
    @input="event => text = event.target.value">

prosto pravim tova, i tolkoz:

    <input v-model="text"></input> 
    
-->
