<script setup lang="ts">
import HoraComponent from '@/components/HoraComponent.vue';
import TiempoComponent from '@/components/TiempoComponent.vue';
import NotasComponent from '@/components/NotasComponent.vue';
console.log(`Hello World from Vue App (Vite + TS)`);
</script>

<template>
    <div class="container pt-4">
        <div class="row">
            <div class="col col-12 mb-4"><h1>Panel de control</h1></div>
        </div>

        <HoraComponent />
        <TiempoComponent />
        <NotasComponent />
    </div>
</template>

<style scoped></style>
