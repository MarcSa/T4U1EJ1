<script setup lang="ts">
import { ref } from 'vue';

const name = ref<string>('John');
setTimeout(() => {
    name.value = 'Alice';
}, 2000);
</script>

<template>
    <section class="card border-warning-subtle border-2">
        <div class="card-body">
            <h2>Variables Reactivas</h2>
            <p>{{ name }}</p>
        </div>
    </section>
</template>

<style scoped></style>
