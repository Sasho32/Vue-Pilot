<script setup>
import { ref } from 'vue';
import UsersList from './UsersList.vue';

const fetchUsers = ref(false);

const clickHandler = () => {
    fetchUsers.value = !fetchUsers.value;
};
</script>

<template>
    <button @click="clickHandler">
        {{ fetchUsers ? 'Hide results' : 'Fetch users' }}
    </button>

    <UsersList v-if="fetchUsers" />
</template>

<style scoped>
h1 {
    font-size: 1.7rem;
    letter-spacing: -1.7px;
}

button {
    cursor: pointer;
    align-self: center;
    padding: 1rem 2rem;
    background-color: blue;
    border-radius: 1rem;
    border: none;
    outline: none;
    font-weight: 700;
}
</style>
