<script setup>
const props = defineProps({
    name: String,
    email: String,
    index: Number,
});

console.log(props.name);
</script>

<template>
    <h2>{{ index }}</h2>
    <div class="user">
        <hr />
        <span class="username">{{ name }}</span>
        <!-- tyka moje da dostypvame i prez var-a -> props.name vypreki che nz za kvo she mi e ama e vyzmojno, ne gyrmi -->
        <span>{{ email }}</span>
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
