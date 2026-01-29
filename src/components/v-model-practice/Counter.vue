<script setup lang="ts">
const counter = defineModel({ default: 0 })
</script>

<template>
    <div class="counter">
        <button class="btn btn-minus" @click="counter--">−</button>
        <span class="value">{{ counter }}</span>
        <button class="btn btn-plus" @click="counter++">+</button>
    </div>
</template>

<style scoped>
.counter {
    display: flex;
    align-items: center;
    gap: 16px;
}

.btn {
    width: 44px;
    height: 44px;
    border: none;
    border-radius: 50%;
    font-size: 24px;
    font-weight: bold;
    cursor: pointer;
    transition:
        transform 0.1s,
        background-color 0.2s;
}

.btn:active {
    transform: scale(0.95);
}

.btn-minus {
    background-color: #ff6b6b;
    color: white;
}

.btn-minus:hover {
    background-color: #ee5a5a;
}

.btn-plus {
    background-color: #42b883;
    color: white;
}

.btn-plus:hover {
    background-color: #3aa876;
}

.value {
    font-size: 32px;
    font-weight: bold;
    min-width: 60px;
    text-align: center;
    color: #333;
}
</style>
