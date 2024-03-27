<script setup>
import { ref, watch } from 'vue';

import BodyMassIndexForm from './components/BodyMassIndexForm.vue'

const bmi = ref('');

// default to imperial units since v-model can't read an initial checked state
const heightUnit = ref('inches');
const weightUnit = ref('pounds');

const useMetric = ref('');

function calculateBMI(height, weight) {
    if (useMetric.value) {
        bmi.value = (weight / (height ** 2)).toFixed(2);
    } else {
        bmi.value = ((weight / (height ** 2)) * 730).toFixed(2);
    }
}

// keep an eye on the checkbox and update units as necessary
watch(useMetric, (useMetric) => {
    if (useMetric) {
        heightUnit.value = 'meters';
        weightUnit.value = 'kilos';
    } else {
        heightUnit.value = 'inches';
        weightUnit.value = 'pounds';
    }

    // clears the old value so the message disappears
    bmi.value = '';
})
</script>

<template>

    <div id="main">
        <h1>Body Mass Index Calculator</h1>
    
        <BodyMassIndexForm
            :heightUnit="heightUnit"
            :weightUnit="weightUnit"
            @stats-entered="calculateBMI">
        </BodyMassIndexForm>
    
        <h3 v-if="bmi">BMI is {{ bmi }}</h3>
    </div>

    <div id="options">
        <h3>Options</h3>
        <input type="checkbox" checked v-model="useMetric" name="units"><label for="units"> Use metric?</label>
    </div>

</template>

<style scoped>
</style>
