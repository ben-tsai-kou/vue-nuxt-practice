<script setup lang="ts">
type Todo = {
    id: number
    text: string
    completed: boolean
    priority: 'low' | 'medium' | 'high'
}

type Emit = {
    toggleComplete: [id: number]
    delete: [id: number]
    updatePriority: [id: number, priority: Todo['priority']]
}

const { todo } = defineProps<{
    todo: Todo
}>()

const emit = defineEmits<Emit>()
</script>

<template>
    <div class="todo-item" :class="{ completed: todo.completed }">
        <input
            type="checkbox"
            :checked="todo.completed"
            @change="emit('toggleComplete', todo.id)"
        />
        <span class="todo-text">{{ todo.text }}</span>
        <select
            :value="todo.priority"
            @change="
                emit(
                    'updatePriority',
                    todo.id,
                    ($event.target as HTMLSelectElement).value as Todo['priority'],
                )
            "
        >
            <option value="low">Low</option>
            <option value="medium">Medium</option>
            <option value="high">High</option>
        </select>
        <button @click="emit('delete', todo.id)">Delete</button>
    </div>
</template>

<style scoped>
.todo-item {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
    margin-bottom: 8px;
}

.todo-item.completed .todo-text {
    text-decoration: line-through;
    color: #888;
}

.todo-text {
    flex: 1;
}
</style>
