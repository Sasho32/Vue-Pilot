<script setup>
import { defineProps } from 'vue';

defineProps({
    user: Object,
    index: Number,
});
</script>

<template>
    <h2>{{ index }}</h2>
    <div class="user">
        <hr />
        <span class="username">{{ user.name }}</span>
        <span>{{ user.email }}</span>
    </div>
</template>

<style scoped>
h2 {
    text-align: center;
}
.user {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1rem;
}

hr {
    align-self: stretch;
}
.username {
    font-weight: 700;
}
</style>
