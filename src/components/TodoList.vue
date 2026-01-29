<script setup lang="ts">
import { ref } from 'vue'
import TodoItem from './TodoItem.vue'

interface Todo {
    id: number
    text: string
    completed: boolean
    priority: 'low' | 'medium' | 'high'
}

const todos = ref<Todo[]>([
    { id: 1, text: 'Learn Vue props', completed: true, priority: 'high' },
    { id: 2, text: 'Practice emit events', completed: false, priority: 'high' },
    { id: 3, text: 'Build a real project', completed: false, priority: 'medium' },
    { id: 4, text: 'Learn Nuxt', completed: false, priority: 'low' },
])

function handleToggleComplete(id: number) {
    todos.value = todos.value.map((item) =>
        item.id === id ? { ...item, completed: !item.completed } : item,
    )
}

function handleDelete(id: number) {
    todos.value = todos.value.filter((item) => item.id !== id)
}

function handleUpdatePriority(id: number, priority: Todo['priority']) {
    todos.value = todos.value.map((item) => (item.id === id ? { ...item, priority } : item))
}
</script>

<template>
    <div class="todo-list">
        <h2>My Todos</h2>
        <TodoItem
            v-for="todo in todos"
            :key="todo.id"
            :todo="todo"
            @toggle-complete="handleToggleComplete"
            @delete="handleDelete"
            @update-priority="handleUpdatePriority"
        />
    </div>
</template>

<style scoped>
.todo-list {
    max-width: 500px;
    margin: 0 auto;
    padding: 20px;
}

h2 {
    margin-bottom: 16px;
}
</style>
