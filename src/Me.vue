<script setup>
import { ref, computed, onUpdated } from 'vue';

const props = defineProps({
    message: Boolean,
});

const firstName = ref('Sasho');
const lastName = ref('Alexandrov');

const profile = ref(1);

const flag = ref(true);

const switchProfile = () => {
    if (profile.value === 1) {
        firstName.value = 'John';
        lastName.value = 'Reese';
        console.log(firstName.value + lastName.value);
        return (profile.value = 2);
    }

    firstName.value = 'Sasho';
    lastName.value = 'Alexandrov';
    console.log(firstName.value + lastName.value);

    profile.value = 1;
};

// computed e za izvlichane na derived state
// kato flname = fn + ln v komponenta v reakt, no daje poveche prilicha na useMemo, zashtoto ne se preizchislyava vs pyt po defolt
// a dependva avtomatichno na state-ovete v nego, bez eksplicitno da se listvat v dependancy array

// ako beshe bez computed samo flname = fn + ln nyamashe za se promeni sled kato izrendi promenite na fn i ln
// runva samo pri update na izpolzvanite v cb stateove

// slojil sym App da my podava prez prop fetchUser state-a si za da vidya kak she runva computed
// 1) ako se izpolzva props v cb-a se runva pri promyana na fetchUser v App(roditelski na tozi)
// i to daje go runva primerno ako imame clg(props.message), a ne samo clg(props)
// 2) ako e kato sega i ne se izpolzva pri rerender ot App zaradi promyana na fetchUser - NE RUNVA computed()
const fullName = computed(() => {
    console.log('running computed');
    console.log(props.message);
    return firstName.value + ' ' + lastName.value;
});

// pri vs state update runva
onUpdated(() => {
    console.log('component state updated!');
});
</script>

<template>
    <span>{{ fullName }}</span>

    <button @click="switchProfile">
        Log in as {{ profile === 1 ? 'John' : 'Sasho' }}
    </button>
    <!-- ako iskame da slojim handlera inline v template-a ne polzvame flag.value a samo flag - stava no nz kolko e dobra praktika-->
    <button @click="() => (flag = !flag)">Change flag - {{ flag }}</button>
</template>

<style scoped>
span {
    color: brown;
}
</style>
