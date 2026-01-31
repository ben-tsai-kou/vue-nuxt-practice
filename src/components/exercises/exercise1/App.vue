<script setup lang="ts">
import ProductCard from './ProductCard.vue'
</script>

<template>
    <div class="demo">
        <h2>完整內容的卡片</h2>
        <ProductCard>
            <template #image>
                <img
                    src="https://pbs.twimg.com/profile_images/1706977520132976641/iCiHHMVi_400x400.jpg"
                />
            </template>
            <template #title> TSG hawks </template>
            <template #default>
                <p>TSG hawks is the best!!</p>
            </template>
            <template #action>
                <a href="https://www.tsghawks.com/" target="_blank">link to web</a>
            </template>
        </ProductCard>

        <h2>只有標題和描述</h2>
        <ProductCard>
            <template #title>
                <p>WBC let's go!!</p>
            </template>

            <template #default> Cant wait! </template>
        </ProductCard>

        <h2>空卡片（全部使用預設內容）</h2>
        <ProductCard />
    </div>
</template>

<style scoped>
.demo {
    padding: 20px;
    display: flex;
    flex-direction: column;
    gap: 32px;
}

h2 {
    font-size: 16px;
    color: #666;
}
</style>
