<script setup>
import { ref } from 'vue';
// @ e alias za src
import UsersList from '@/UsersList.vue';
import personPic from '@/assets/person.png';
// taka se importva pic za da imame primerno :href="personPic" a ne href="./assets/....png"
import RandomMessage from '@/RandomMessage.vue';
import Wrapper from '@/Wrapper.vue';
import Me from '@/Me.vue';

import ParentInput from './components/ParentInput.vue';

const fetchUsers = ref(false);

const clickHandler = () => {
    fetchUsers.value = !fetchUsers.value;
};
</script>

<template>
    <ParentInput />
    <!-- html attr ili prop podaden s : -> vs v kavichkite e js -->
    <Me :message="fetchUsers" />
    <RandomMessage :message="fetchUsers" />
    <Wrapper :status="{ message: 'completed' }">
        <h3>Inside wrapper slot...</h3>
    </Wrapper>
    <img v-if="fetchUsers" :src="personPic" alt="kzl" data-green />
    <!-- na style moje da podavame i obekt podobno na reakt(ne pomna bash kak beshe tam, ideyata e che moje da dependva na nekvi state-ove stilizaciyata) -->
    <button
        :style="{
            backgroundColor: fetchUsers ? 'red' : 'blue',
        }"
        @click="clickHandler"
    >
        {{ fetchUsers ? 'Hide results' : 'Fetch the users' }}
    </button>

    <UsersList v-if="fetchUsers" />
</template>

<style scoped>
/* kato e scoped ne moje da acessva elementi na po gorni niva - v slychaya html, body i tn */
[data-green] {
    width: 100px;
    background-color: green;
    padding: 1rem;
    box-sizing: content-box;
    border-radius: 50%;
}

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
    outline: 2px solid #fff;
    font-weight: 700;
}
</style>
