<script setup>
import { onBeforeUnmount } from 'vue';
import { onBeforeMount, onMounted, onUnmounted, ref } from 'vue';
import User from './User.vue';

const users = ref([]);
const loading = ref(true);

onMounted(async () => {
    console.log('%cOn mounted', 'background:blue;');
    try {
        const response = await fetch(
            'https://jsonplaceholder.typicode.com/users'
        );
        const usersArray = await response.json();

        users.value = [...usersArray];
    } catch (e) {
        console.log('Error fetching the users...', e);
    } finally {
        loading.value = false;
    }
});

onBeforeMount(() => {
    console.log('%cOn before mounted', 'background:red;');
});

onBeforeMount(() => {
    console.log('On before mounted 2');
});

onUnmounted(() => {
    console.log('%cOn unmounted', 'background:green;');
});

onBeforeUnmount(() => {
    console.log('%cOn before unmounted', 'background:lightgreen;');
});
</script>

<template>
    <h1 v-if="loading">Fetching users...</h1>
    <User
        v-else
        v-for="({ id, name, email }, index) in users"
        :key="id"
        :name="name"
        :email="email"
        :index="index"
    />
</template>
