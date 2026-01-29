<script setup lang="ts">
import { ref } from 'vue'
import CustomInput from './CustomInput.vue'
import Counter from './Counter.vue'
import UserForm from './UserForm.vue'
import ModifiableInput from './ModifiableInput.vue'
import ColorPicker from './ColorPicker.vue'

// 練習 1
const customInputValue = ref('')

// 練習 2
const counterValue = ref(0)

// 練習 3
const firstName = ref('')
const lastName = ref('')

// 練習 4
const text1 = ref('')
const text2 = ref('')
const text3 = ref('')
const text4 = ref('')

// 練習 5
const red = ref(0)
const green = ref(0)
const blue = ref(0)
</script>

<template>
    <div class="practice-container">
        <h1 class="main-title">v-model 練習</h1>

        <!-- 練習 1 -->
        <section class="section">
            <h2 class="section-title">練習 1：Custom Input</h2>
            <CustomInput v-model="customInputValue" />
            <p class="parent-display">父組件的值：「{{ customInputValue }}」</p>
        </section>

        <!-- 練習 2 -->
        <section class="section">
            <h2 class="section-title">練習 2：Counter</h2>
            <Counter v-model="counterValue" />
            <p class="parent-display">父組件的值：{{ counterValue }}</p>
        </section>

        <!-- 練習 3 -->
        <section class="section">
            <h2 class="section-title">練習 3：User Form (Multiple v-models)</h2>
            <UserForm v-model:first-name="firstName" v-model:last-name="lastName" />
            <p class="parent-display">Full Name：{{ firstName }} {{ lastName }}</p>
        </section>

        <!-- 練習 4 -->
        <section class="section">
            <h2 class="section-title">練習 4：Modifiable Input</h2>

            <div class="modifier-group">
                <span class="modifier-label">無 modifier：</span>
                <ModifiableInput v-model="text1" />
                <span class="result">→ 「{{ text1 }}」</span>
            </div>

            <div class="modifier-group">
                <span class="modifier-label">.uppercase：</span>
                <ModifiableInput v-model.uppercase="text2" />
                <span class="result">→ 「{{ text2 }}」</span>
            </div>

            <div class="modifier-group">
                <span class="modifier-label">.trim：</span>
                <ModifiableInput v-model.trim="text3" />
                <span class="result">→ 「{{ text3 }}」</span>
            </div>

            <div class="modifier-group">
                <span class="modifier-label">.uppercase.trim：</span>
                <ModifiableInput v-model.uppercase.trim="text4" />
                <span class="result">→ 「{{ text4 }}」</span>
            </div>
        </section>

        <!-- 練習 5 -->
        <section class="section">
            <h2 class="section-title">練習 5：Color Picker (3 個 v-models)</h2>
            <ColorPicker v-model:red="red" v-model:green="green" v-model:blue="blue" />
            <p class="parent-display">父組件的值：RGB({{ red }}, {{ green }}, {{ blue }})</p>
            <div
                class="color-display"
                :style="{ backgroundColor: `rgb(${red}, ${green}, ${blue})` }"
            >
                RGB({{ red }}, {{ green }}, {{ blue }})
            </div>
        </section>
    </div>
</template>

<style scoped>
.practice-container {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
}

.main-title {
    text-align: center;
    color: #42b883;
    margin-bottom: 32px;
}

.section {
    background: #f9f9f9;
    border-radius: 12px;
    padding: 20px;
    margin-bottom: 24px;
}

.section-title {
    font-size: 18px;
    color: #333;
    margin: 0 0 16px 0;
    padding-bottom: 8px;
    border-bottom: 2px solid #42b883;
}

.parent-display {
    margin: 16px 0 0 0;
    padding: 12px;
    background: #fff;
    border-radius: 8px;
    border-left: 4px solid #42b883;
    color: #333;
}

.modifier-group {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 12px;
    flex-wrap: wrap;
}

.modifier-label {
    font-size: 14px;
    font-weight: 600;
    color: #555;
    min-width: 140px;
}

.modifier-group .modifiable-input {
    flex: 1;
    min-width: 150px;
}

.result {
    font-size: 14px;
    color: #42b883;
    font-weight: 500;
}

.color-display {
    margin-top: 12px;
    padding: 20px;
    border-radius: 8px;
    text-align: center;
    font-weight: bold;
    color: white;
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
    border: 2px solid #e0e0e0;
}
</style>
