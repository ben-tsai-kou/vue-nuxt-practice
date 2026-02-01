<script setup lang="ts">
import { ref, onMounted } from 'vue'
import UserList from './UserList.vue'

const isLoading = ref(true)
const users = ref([
    { id: 1, name: 'Alice Chen', email: 'alice@example.com', role: 'admin' as const, avatar: '👩‍💼' },
    { id: 2, name: 'Bob Wang', email: 'bob@example.com', role: 'user' as const, avatar: '👨‍💻' },
    { id: 3, name: 'Carol Lin', email: 'carol@example.com', role: 'user' as const, avatar: '👩‍🎨' },
    { id: 4, name: 'David Lee', email: 'david@example.com', role: 'guest' as const, avatar: '👨‍🎓' },
    { id: 5, name: 'Emma Wu', email: 'emma@example.com', role: 'admin' as const, avatar: '👩‍🔬' },
])

onMounted(() => {
    setTimeout(() => {
        isLoading.value = false
    }, 1000)
})
</script>

<template>
    <div class="demo">
        <h1>User Management</h1>

        <UserList :users="users" :loading="isLoading">
            <!-- TODO: 實作三個 slots
        1. loading slot: 顯示 "Loading users..."
        2. user slot (scoped): 顯示使用者卡片，包含 avatar (可用 emoji)、name、email、role badge
        3. empty slot: 顯示 "No users found" 訊息
      -->

            <!-- 1 -->
            <template #loading>
                <p>loading users...</p>
            </template>
            <!-- 2 -->
            <template #user="{ name, email, role, avatar }">
                <div>
                    <span>{{ name }}</span>
                    <span>{{ email }}</span>
                    <span>{{ role }}</span>
                    <span>{{ avatar }}</span>
                </div>
            </template>
            <!-- 3 -->
            <template #default>
                <p>no users found</p>
            </template>
        </UserList>
    </div>
</template>

<style scoped>
.demo {
    padding: 20px;
    max-width: 800px;
    margin: 0 auto;
    color: #000;
}

h1 {
    margin-bottom: 24px;
}
</style>
