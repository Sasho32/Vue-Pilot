<script setup>
import { onBeforeUnmount } from 'vue';
import { onBeforeMount, onMounted, onUnmounted, ref } from 'vue';

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

onUnmounted(() => {
    console.log('%cOn unmounted', 'background:green;');
});

onBeforeUnmount(() => {
    console.log('%cOn before unmounted', 'background:lightgreen;');
});
</script>

<template>
    <h1 v-if="loading">Fetching users...</h1>
    <ul v-else id="users" v-for="(user, index) in users" :key="user.id">
        <h2>{{ index }}</h2>
        <li class="user">
            <hr />
            <span>{{ user.name }}</span>
            <span>{{ user.email }}</span>
        </li>
    </ul>
</template>

<style scoped>
h2 {
    text-align: center;
}
ul {
    list-style: none;
    padding: 2rem 25vw;
}
li {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1rem;
}

hr {
    align-self: stretch;
}
span:first-of-type {
    font-weight: 700;
}
</style>
