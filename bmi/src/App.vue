<script setup>
import { ref } from 'vue';

import BodyMassIndexForm from './components/BodyMassIndexForm.vue'

const bmi = ref('');

function calculateBMI(height, weight) {
    bmi.value = (weight / ( height ** 2 )).toFixed(2);
}
</script>

<template>

    <h1>Body Mass Index Calculator</h1>

    <BodyMassIndexForm
        @stats-entered="calculateBMI">
    </BodyMassIndexForm>

    <h3 v-if="bmi">BMI is {{ bmi }}</h3>

</template>

<style scoped>
</style>
