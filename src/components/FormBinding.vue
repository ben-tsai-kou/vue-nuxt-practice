<script setup lang="ts">
import { ref } from 'vue'

// TODO: 在這裡定義你的 ref，然後在 template 中加上 v-model
// 需要處理的欄位：
// 1. name - 姓名 (string)
// 2. bio - 自我介紹 (string)
// 3. subscribe - 訂閱電子報 (boolean)
// 4. languages - 喜歡的程式語言 (string[]) - 可複選
// 5. level - 經驗等級 (string) - 單選
// 6. city - 所在城市 (string) - 下拉選單
const name = ref('')
const bio = ref('')
const subscribe = ref(false)
const languages = ref([])
const level = ref('')
const city = ref('')
</script>

<template>
    <template>
        <h1>開發者資料表單</h1>
        <p class="subtitle">練習 v-model 雙向綁定</p>

        <form class="form" @submit.prevent>
            <!-- 1. Text Input: 姓名 -->
            <div class="field">
                <label>姓名</label>
                <input type="text" placeholder="請輸入姓名" v-model="name" />
                <div class="preview">name: {{ name }}</div>
            </div>

            <!-- 2. Textarea: 自我介紹 -->
            <div class="field">
                <label>自我介紹</label>
                <textarea rows="3" placeholder="簡單介紹一下自己..." v-model="bio"></textarea>
                <div class="preview">bio: {{ bio }}</div>
            </div>

            <!-- 3. Single Checkbox: 訂閱電子報 -->
            <div class="field">
                <label class="checkbox-label">
                    <input type="checkbox" v-model="subscribe" />
                    訂閱電子報
                </label>
                <div class="preview">subscribe: {{ subscribe }}</div>
            </div>

            <!-- 4. Multiple Checkbox: 喜歡的程式語言 -->
            <div class="field">
                <label>喜歡的程式語言（可複選）</label>
                <div class="checkbox-group">
                    <label class="checkbox-label">
                        <input type="checkbox" value="javascript" v-model="languages" />
                        JavaScript
                    </label>
                    <label class="checkbox-label">
                        <input type="checkbox" value="typescript" v-model="languages" />
                        TypeScript
                    </label>
                    <label class="checkbox-label">
                        <input type="checkbox" value="python" v-model="languages" />
                        Python
                    </label>
                    <label class="checkbox-label">
                        <input type="checkbox" value="go" v-model="languages" />
                        Go
                    </label>
                </div>
                <div class="preview">languages: {{ languages }}</div>
            </div>

            <!-- 5. Radio: 經驗等級 -->
            <div class="field">
                <label>經驗等級</label>
                <div class="radio-group">
                    <label class="radio-label">
                        <input type="radio" value="junior" v-model="level" />
                        Junior (0-2年)
                    </label>
                    <label class="radio-label">
                        <input type="radio" value="mid" v-model="level" />
                        Mid (2-5年)
                    </label>
                    <label class="radio-label">
                        <input type="radio" value="senior" v-model="level" />
                        Senior (5年以上)
                    </label>
                </div>
                <div class="preview">level: {{ level }}</div>
            </div>

            <!-- 6. Select: 所在城市 -->
            <div class="field">
                <label>所在城市</label>
                <select v-model="city">
                    <option disabled value="">請選擇</option>
                    <option value="taipei">台北</option>
                    <option value="taichung">台中</option>
                    <option value="kaohsiung">高雄</option>
                    <option value="other">其他</option>
                </select>
                <div class="preview">city: {{ city }}</div>
            </div>

            <button type="submit" class="submit-btn">送出</button>
        </form>
    </template>
</template>

<style scoped>
h1 {
    color: #42b883;
    margin-bottom: 5px;
}

.subtitle {
    color: #666;
    margin-top: 0;
    margin-bottom: 30px;
}

.form {
    display: flex;
    flex-direction: column;
    gap: 20px;
}

.field {
    display: flex;
    flex-direction: column;
    gap: 8px;
}

.field > label {
    font-weight: 600;
    color: #2c3e50;
}

input[type='text'],
textarea,
select {
    padding: 10px;
    border: 2px solid #ddd;
    border-radius: 6px;
    font-size: 1em;
    transition: border-color 0.2s;
}

input:focus,
textarea:focus,
select:focus {
    outline: none;
    border-color: #42b883;
}

.checkbox-group,
.radio-group {
    display: flex;
    flex-wrap: wrap;
    gap: 15px;
}

.checkbox-label,
.radio-label {
    display: flex;
    align-items: center;
    gap: 6px;
    cursor: pointer;
    font-weight: normal;
}

input[type='checkbox'],
input[type='radio'] {
    width: 18px;
    height: 18px;
    cursor: pointer;
}

.preview {
    padding: 8px 12px;
    background: #2c3e50;
    color: #42b883;
    border-radius: 4px;
    font-family: 'Monaco', 'Consolas', monospace;
    font-size: 0.85em;
}

.submit-btn {
    padding: 12px;
    background: #42b883;
    color: white;
    border: none;
    border-radius: 6px;
    font-size: 1em;
    font-weight: 600;
    cursor: pointer;
    transition: background 0.2s;
}

.submit-btn:hover {
    background: #3aa876;
}
</style>
