<script setup lang="ts">
import { ref } from 'vue'
import Exercise1 from './components/exercises/exercise1/App.vue'
import Exercise2 from './components/exercises/exercise2/App.vue'
import Exercise3 from './components/exercises/exercise3/App.vue'
import Exercise4 from './components/exercises/exercise4/App.vue'

const currentExercise = ref(1)
</script>

<template>
    <div class="app">
        <div class="exercise-selector">
            asdfasdf
            <h1>Vue Slots 練習</h1>
            <div class="buttons">
                <button
                    v-for="i in 4"
                    :key="i"
                    :class="{ active: currentExercise === i }"
                    @click="currentExercise = i"
                >
                    練習 {{ i }}
                </button>
            </div>
        </div>

        <div class="exercise-content">
            <Exercise1 v-if="currentExercise === 1" />
            <Exercise2 v-if="currentExercise === 2" />
            <Exercise3 v-if="currentExercise === 3" />
            <Exercise4 v-if="currentExercise === 4" />
        </div>
    </div>
</template>

<style scoped>
.app {
    min-height: 100vh;
    background: #f9f9f9;
}

.exercise-selector {
    background: white;
    padding: 24px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    margin-bottom: 24px;
}

.exercise-selector h1 {
    margin: 0 0 16px 0;
    font-size: 24px;
    color: #333;
}

.buttons {
    display: flex;
    gap: 12px;
}

.buttons button {
    padding: 10px 20px;
    border: 2px solid #42b883;
    background: white;
    color: #42b883;
    border-radius: 6px;
    cursor: pointer;
    font-size: 14px;
    font-weight: 600;
    transition: all 0.2s;
}

.buttons button:hover {
    background: #f0faf6;
}

.buttons button.active {
    background: #42b883;
    color: white;
}

.exercise-content {
    padding: 0 24px 24px;
}
</style>
