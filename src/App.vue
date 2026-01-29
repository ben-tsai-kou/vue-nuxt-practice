<script setup lang="ts">
// import FormBinding from './components/FormBinding.vue'
import TodoList from './components/TodoList.vue'
</script>

<template>
    <div class="container">
        <!-- <FormBinding /> -->
        <TodoList />
    </div>
</template>

<style scoped>
.container {
    max-width: 500px;
    margin: 0 auto;
    padding: 20px;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}
</style>
