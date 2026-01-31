<script setup lang="ts">
interface Props {
    columns: string[]
    data: Record<string, unknown>[]
}

defineProps<Props>()
</script>

<template>
    <table class="data-table">
        <thead>
            <tr>
                <th v-for="column in columns" :key="column">
                    {{ column }}
                </th>
            </tr>
        </thead>
        <tbody>
            <!-- TODO: 用 v-for 渲染每一行，並將 row data, row index 傳給 scoped slot -->
        </tbody>
    </table>
</template>

<style scoped>
.data-table {
    width: 100%;
    border-collapse: collapse;
}

.data-table th {
    background: #f5f5f5;
    padding: 12px;
    text-align: left;
    border-bottom: 2px solid #ddd;
    font-weight: 600;
}

.data-table td {
    padding: 12px;
    border-bottom: 1px solid #eee;
}

.data-table tbody tr:hover {
    background: #fafafa;
}
</style>
