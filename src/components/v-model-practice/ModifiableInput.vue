<script setup lang="ts">
const [model, modifiers] = defineModel({
    set(value) {
        if (typeof value === 'string') {
            if (modifiers.uppercase && modifiers.trim) {
                return value.toUpperCase().trim()
            }

            if (modifiers.uppercase) {
                return value.toUpperCase()
            }

            if (modifiers.trim) {
                return value.trim()
            }
        }
        return value
    },
})
</script>

<template>
    <div class="modifiable-input">
        <input type="text" class="input" placeholder="輸入文字..." v-model="model" />
    </div>
</template>

<style scoped>
.modifiable-input {
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
</style>
