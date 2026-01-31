<script setup lang="ts">
import { ref, computed } from 'vue'

interface User {
    id: number
    name: string
    email: string
    role: 'admin' | 'user' | 'guest'
    avatar?: string
}

interface Props {
    users: User[]
    loading?: boolean
}

const props = withDefaults(defineProps<Props>(), {
    loading: false,
})

const searchQuery = ref('')
const roleFilter = ref('')

// TODO: 實作 filteredUsers computed property
// 根據 searchQuery (name) 和 roleFilter 過濾 users
const filteredUsers = computed(() => {
    // 你的實作
    return []
})
</script>

<template>
    <div class="user-list">
        <div class="filters">
            <input
                v-model="searchQuery"
                type="text"
                placeholder="Search by name..."
                class="search-input"
            />
            <select v-model="roleFilter" class="role-filter">
                <option value="">All Roles</option>
                <option value="admin">Admin</option>
                <option value="user">User</option>
                <option value="guest">Guest</option>
            </select>
        </div>

        <div class="list-container">
            <!-- TODO: 實作三種狀態
        1. loading 狀態：使用 loading slot
        2. 有過濾結果：使用 v-for 渲染，每個 user 用 scoped slot 傳出去
        3. 沒有結果：使用 empty slot
      -->
        </div>
    </div>
</template>

<style scoped>
.user-list {
    border: 1px solid #ddd;
    border-radius: 8px;
    overflow: hidden;
}

.filters {
    padding: 16px;
    background: #f5f5f5;
    display: flex;
    gap: 12px;
    border-bottom: 1px solid #ddd;
}

.search-input {
    flex: 1;
    padding: 8px 12px;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 14px;
}

.role-filter {
    padding: 8px 12px;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 14px;
    background: white;
}

.list-container {
    min-height: 200px;
}
</style>
