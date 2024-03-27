<script setup>
import { ref } from 'vue';

defineProps({
    height: Number,
    weight: Number,
    heightUnit: String,
    weightUnit: String
});

const emit = defineEmits([
    'stats-entered'
]);

const height = ref();
const weight = ref();

function statsEntered() {
    // check to make sure the boxes aren't empty, rudimentary input validation
    if (height.value !== undefined && weight.value !== undefined) {
        emit('stats-entered', height.value, weight.value);
        console.log('Height and weight entered, emitting to App.vue...');
    }
}
</script>

<template>
    <h2>Enter your height and weight</h2>
    <p>
        <label for="bmi-height">Height (in {{ heightUnit }}) </label>
        <input name="bmi-height" v-model="height">
        <br>
        <label for="bmi-weight">Weight (in {{ weightUnit }}) </label>
        <input name="bmi-weight" v-model="weight">
    </p>
    <button @click="statsEntered">Calculate</button>
</template>

<style scoped>
</style>
