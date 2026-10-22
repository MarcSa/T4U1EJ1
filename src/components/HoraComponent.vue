<script setup lang="ts">
import { ref } from 'vue';

const h = ref<string>('0');
const m = ref<string>('0');
const s = ref<string>('0');
const timeout: number = 1000;

const time = () => {
    const today = new Date();
    h.value = today.getHours().toString();
    m.value = checkTime(today.getMinutes());
    s.value = checkTime(today.getSeconds());
    setTimeout(time, timeout);
};

setTimeout(time, 1);

const checkTime = (i: number): string => {
    if (i < 10) {
        return '0' + i.toString();
    } // add zero in front of numbers < 10
    return i.toString();
};
</script>

<template>
    <section
        class="border-2 border-start p-4 rounded-4 border-warning bd-yellow-100 mb-3"
        style="background-color: #fff3cd"
    >
        <h6>Hora</h6>
        <p class="mb-0">{{ h }}h {{ m }}' {{ s }}''</p>
    </section>
</template>

<style scoped></style>
