<script setup lang="ts">
import { ref } from 'vue'

interface Props {
    tabs: string[]
    defaultTab?: string
}

const { tabs, defaultTab } = defineProps<Props>()

const activeTab = ref(defaultTab ?? tabs[0])
</script>

<template>
    <div class="tabs">
        <div class="tab-buttons">
            <button
                v-for="tab in tabs"
                :key="tab"
                :class="{ active: activeTab === tab }"
                @click="activeTab = tab"
            >
                {{ tab }}
            </button>
        </div>

        <div class="tab-content">
            <!-- TODO: 根據 activeTab 動態顯示對應的 slot 內容 -->
            <slot :name="activeTab">
                <p>this is only for {{ activeTab }}</p>
            </slot>
        </div>
    </div>
</template>

<style scoped>
.tabs {
    border: 1px solid #ddd;
    border-radius: 8px;
    overflow: hidden;
}

.tab-buttons {
    display: flex;
    background: #f5f5f5;
    border-bottom: 1px solid #ddd;
}

.tab-buttons button {
    flex: 1;
    padding: 12px 16px;
    border: none;
    background: transparent;
    cursor: pointer;
    font-size: 14px;
    transition: background 0.2s;
}

.tab-buttons button:hover {
    background: #e8e8e8;
}

.tab-buttons button.active {
    background: white;
    font-weight: bold;
}

.tab-content {
    padding: 20px;
    min-height: 150px;
}
</style>
