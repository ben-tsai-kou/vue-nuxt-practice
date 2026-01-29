<script setup lang="ts">
const firstName = defineModel('firstName')
const lastName = defineModel('lastName')
</script>

<template>
    <div class="user-form">
        <div class="field">
            <label class="label">First Name</label>
            <input type="text" class="input" placeholder="輸入名字..." v-model="firstName" />
        </div>
        <div class="field">
            <label class="label">Last Name</label>
            <input type="text" class="input" placeholder="輸入姓氏..." v-model="lastName" />
        </div>
    </div>
</template>

<style scoped>
.user-form {
    display: flex;
    flex-direction: column;
    gap: 16px;
}

.field {
    display: flex;
    flex-direction: column;
    gap: 6px;
}

.label {
    font-size: 14px;
    font-weight: 600;
    color: #555;
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
