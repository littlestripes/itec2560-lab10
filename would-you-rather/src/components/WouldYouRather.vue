<script setup>
import { ref, watch } from 'vue';

defineProps({
    question: String,
    answer1: String,
    answer2: String
});

const emit = defineEmits([
    'answer-selected'
]);

const choice = ref('');

/*function choiceMade() {*/
    /*emit('answer-selected', choice.value);*/
/*}*/

watch(choice, () => {
    emit('answer-selected', choice.value);
});
</script>

<template>
    <div id="wyr">
        <h2>Make your choice!</h2>
    
        {{ question }}
    
        <input type="radio" id="answer-1" v-model="choice" :value="answer1">
        <label for="answer-1">{{ answer1 }}</label>
        <input type="radio" id="answer-2" v-model="choice" :value="answer2">
        <label for="answer-2">{{ answer2 }}</label>
    </div>
</template>

<style scoped>
#wyr {
    background-color: #444444;
}
</style>
