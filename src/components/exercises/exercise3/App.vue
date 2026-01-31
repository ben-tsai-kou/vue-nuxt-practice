<script setup lang="ts">
import { ref } from 'vue'
import DataTable from './DataTable.vue'

const users = ref([
    { id: 1, name: 'Alice Chen', email: 'alice@example.com', active: true },
    { id: 2, name: 'Bob Wang', email: 'bob@example.com', active: false },
    { id: 3, name: 'Carol Lin', email: 'carol@example.com', active: true },
])
</script>

<template>
    <div class="demo">
        <h2>User Table</h2>
        <DataTable :columns="['Name', 'Email', 'Status', 'Actions']" :data="users">
            <!-- TODO: 用 scoped slot 自訂每一行的顯示方式 -->
            <!-- 需求：
        - Name: 顯示 user.name
        - Email: 顯示 user.email
        - Status: 如果 user.active 是 true 顯示綠色的 "Active"，否則顯示灰色的 "Inactive"
        - Actions: 顯示 "Edit" 和 "Delete" 按鈕
      -->
        </DataTable>
    </div>
</template>

<style scoped>
.demo {
    padding: 20px;
}

h2 {
    margin-bottom: 16px;
}
</style>
