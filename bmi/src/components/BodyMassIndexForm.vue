<script setup>
import { ref } from 'vue';

defineProps({
    height: Number,
    weight: Number
});

const emit = defineEmits([
    'stats-entered'
]);

const height = ref();
const weight = ref();

function statsEntered() {
    emit('stats-entered', height.value, weight.value);
    console.log('Height and weight entered, emitting to App.vue...');
}
</script>

<template>
    <h2>Enter your height and weight</h2>
    <p>
        <label for="bmi-height">Height (in meters) </label><input name="bmi-height" v-model="height">
        <br>
        <label for="bmi-weight">Weight (in kilos) </label><input name="bmi-weight" v-model="weight">
    </p>
    <button @click="statsEntered">Calculate</button>
</template>

<style scoped>
</style>
