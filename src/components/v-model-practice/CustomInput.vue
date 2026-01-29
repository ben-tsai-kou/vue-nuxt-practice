<script setup lang="ts">
const customInputValue = defineModel()
</script>

<template>
    <div class="custom-input">
        <input type="text" class="input" placeholder="輸入文字..." v-model="customInputValue" />
        <p class="display">
            目前綁定的值：<span>{{ customInputValue }}</span>
        </p>
    </div>
</template>

<style scoped>
.custom-input {
    display: flex;
    flex-direction: column;
    gap: 8px;
}

.input {
    padding: 10px 14px;
    border: 2px solid #e0e0e0;
    border-radius: 8px;
    font-size: 16px;
    transition: border-color 0.2s;
}

.input:focus {
    outline: none;
    border-color: #42b883;
}

.display {
    margin: 0;
    color: #666;
    font-size: 14px;
}

.display span {
    color: #42b883;
    font-weight: 600;
}
</style>
