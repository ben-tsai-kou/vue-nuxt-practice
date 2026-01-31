<script setup lang="ts">
import DynamicTabs from './DynamicTabs.vue'
</script>

<template>
    <div class="demo">
        <DynamicTabs :tabs="['Profile', 'Settings', 'Notifications']">
            <template #Profile>
                <p class="text-color">this is only for profile</p>
            </template>
            <template #Settings>
                <p class="text-color">this is only for Settings</p>
            </template>
            <template #Notifications>
                <p class="text-color">this is only for Notifications</p>
            </template>
        </DynamicTabs>
    </div>
</template>

<style scoped>
.text-color {
    color: red;
}

.demo {
    padding: 20px;
    max-width: 600px;
}
</style>
