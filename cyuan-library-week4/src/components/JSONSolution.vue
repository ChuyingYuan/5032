<template>
    <div>
        <h1>JSON Solution</h1>
        <textarea v-model="jsonInput" placeholder="Enter JSON here"></textarea>
        <button @click="parseJson">Parse JSON</button>
        <div v-if="jsonError" class="error">{{ jsonError }}</div>
        <pre v-if="parsedJson">{{ parsedJson }}</pre>
    </div>
</template>

<script setup>
import { ref } from 'vue'

const jsonInput = ref('')
const parsedJson = ref(null)
const jsonError = ref('')

const parseJson = () => {
    try {
        parsedJson.value = JSON.parse(jsonInput.value)
        jsonError.value = ''
    } catch (error) {
        jsonError.value = 'Invalid JSON'
        parsedJson.value = null
    }
}
</script>

<style scoped>
textarea {
    width: 100%;
    height: 150px;
    margin-bottom: 10px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

button {
    padding: 10px 15px;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

button:hover {
    background-color: #45a049;
}

.error {
    color: red;
    margin-top: 10px;
}

pre {
    background-color: #f4f4f4;
    padding: 10px;
    border-radius: 4px;
}
</style>