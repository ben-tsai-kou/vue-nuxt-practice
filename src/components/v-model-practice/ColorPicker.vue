<script setup lang="ts">
// 練習 5：Color Picker（Multiple v-models with 3 values）
// TODO: 實作 v-model:red、v-model:green、v-model:blue 三個綁定
// 每個值的範圍是 0-255

const red = defineModel('red')
const green = defineModel('green')
const blue = defineModel('blue')
</script>

<template>
    <div class="color-picker">
        <div class="sliders">
            <div class="slider-group">
                <label class="label">
                    <span class="label-text">Red:</span>
                    <span class="value">{{ red }}</span>
                </label>
                <input type="range" min="0" max="255" class="slider slider-red" v-model="red" />
            </div>

            <div class="slider-group">
                <label class="label">
                    <span class="label-text">Green:</span>
                    <span class="value">{{ green }}</span>
                </label>
                <input type="range" min="0" max="255" class="slider slider-green" v-model="green" />
            </div>

            <div class="slider-group">
                <label class="label">
                    <span class="label-text">Blue:</span>
                    <span class="value">{{ blue }}</span>
                </label>
                <input type="range" min="0" max="255" class="slider slider-blue" v-model="blue" />
            </div>
        </div>

        <div class="preview" :style="{ backgroundColor: `rgb(${red}, ${green}, ${blue})` }">
            <span class="preview-text">Preview</span>
        </div>
    </div>
</template>

<style scoped>
.color-picker {
    display: flex;
    flex-direction: column;
    gap: 20px;
}

.sliders {
    display: flex;
    flex-direction: column;
    gap: 16px;
}

.slider-group {
    display: flex;
    flex-direction: column;
    gap: 8px;
}

.label {
    display: flex;
    justify-content: space-between;
    font-size: 14px;
    font-weight: 600;
    color: #555;
}

.label-text {
    color: #333;
}

.value {
    color: #42b883;
    font-family: 'Courier New', monospace;
}

.slider {
    width: 100%;
    height: 8px;
    border-radius: 4px;
    outline: none;
    -webkit-appearance: none;
    cursor: pointer;
}

.slider::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
    width: 20px;
    height: 20px;
    border-radius: 50%;
    background: white;
    border: 2px solid currentColor;
    cursor: pointer;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}

.slider::-moz-range-thumb {
    width: 20px;
    height: 20px;
    border-radius: 50%;
    background: white;
    border: 2px solid currentColor;
    cursor: pointer;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}

.slider-red {
    background: linear-gradient(to right, #000, #ff0000);
    color: #ff0000;
}

.slider-green {
    background: linear-gradient(to right, #000, #00ff00);
    color: #00ff00;
}

.slider-blue {
    background: linear-gradient(to right, #000, #0000ff);
    color: #0000ff;
}

.preview {
    height: 120px;
    border-radius: 12px;
    display: flex;
    align-items: center;
    justify-content: center;
    border: 2px solid #e0e0e0;
    transition: background-color 0.2s;
}

.preview-text {
    font-size: 24px;
    font-weight: bold;
    color: white;
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
}
</style>
