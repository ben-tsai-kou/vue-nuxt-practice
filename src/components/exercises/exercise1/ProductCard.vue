<script setup lang="ts">
defineOptions({
    name: 'ProductCard',
})
</script>

<template>
    <div class="product-card">
        <div class="product-image">
            <slot name="image"> No Image </slot>
        </div>

        <div class="product-content">
            <h3 class="product-title">
                <slot name="title">Untitled Product</slot>
            </h3>

            <div class="product-description">
                <slot> No description available </slot>
            </div>
        </div>

        <div class="product-actions">
            <slot name="action">
                <button>view detail</button>
            </slot>
        </div>
    </div>
</template>

<style scoped>
.product-card {
    border: 1px solid #ddd;
    border-radius: 8px;
    overflow: hidden;
    max-width: 300px;
}

.product-image {
    height: 500px;
    background: #f5f5f5;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #999;
}

.product-content {
    padding: 16px;
}

.product-title {
    margin: 0 0 8px 0;
    color: #333;
}

.product-description {
    color: #666;
    font-size: 14px;
}

.product-actions {
    padding: 16px;
    border-top: 1px solid #eee;
    display: flex;
    gap: 8px;
}
</style>
