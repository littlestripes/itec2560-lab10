<script setup>
import { ref } from 'vue'

import WouldYouRather from './components/WouldYouRather.vue'

// question and two answers
const wyrQuestion = ref('Would you rather be able to see new colors that no other people could see or be able to hear things that no other humans can hear?');
const wyrAnswer1 = ref('Colors');
const wyrAnswer2 = ref('Hearing');

// for the user's selection
const userSelection = ref('');

function updateUserSelection(userChoice) {
    userSelection.value = `Thanks! You chose ${userChoice}`;
}
</script>

<template>
    <div id="app">

        <h1>Would You Rather...</h1>

        <would-you-rather
            :question="wyrQuestion"
            :answer1="wyrAnswer1"
            :answer2="wyrAnswer2"
            @answer-selected="updateUserSelection">
        </would-you-rather>

        {{ userSelection }}

    </div>
</template>

<style scoped>
#app {
    background-color: grey;
}
</style>
