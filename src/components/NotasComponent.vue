<script setup lang="ts">
import { ref } from 'vue';
import type { Note } from '@/interfaces/note.interface';

const notes = ref<Note[]>([]);
const text = ref<string>('');

const getNextId = (): number => {
    const orderedByIdNotes = [...notes.value].sort((a, b) => a.id - b.id);
    const lastNote = orderedByIdNotes[orderedByIdNotes.length - 1];

    return lastNote ? lastNote.id + 1 : 1;
};

const addNote = () => {
    notes.value.push({
        id: getNextId(),
        text: text.value,
        time: Date.now(),
    });
    text.value = '';
};
const deleteNote = (id: number) => {
    const noteIndex = notes.value.findIndex((obj) => obj.id === id);
    notes.value.splice(noteIndex, 1);
};

const displayNotes = (): boolean => notes.value.length !== 0;
</script>

<template>
    <section
        class="border-2 border-start p-4 rounded-4 mb-3"
        style="background-color: #cfe2ff; border-color: #0d6efd !important"
    >
        <h6>Notas</h6>
        <textarea
            name="text"
            id="text"
            rows="5"
            style="width: 100%; border-color: #0d6efd"
            class="rounded-2"
            v-model="text"
        ></textarea>
        <div class="mb-4">
            <input type="submit" value="Agregar" class="btn btn-lg btn-primary" @click="addNote" />
        </div>
        <p class="text-center mb-4">Total notas: {{ notes.length }}</p>
        <div v-if="displayNotes()">
            <div
                class="mb-2 bg-white rounded-2 py-3 px-3 d-flex flex-row justify-content-between align-items-center"
                v-for="note in notes"
                :key="note.id"
            >
                <p class="text-note mb-0">{{ note.text }}</p>
                <div class="d-flex flex-row justify-content-between align-items-center">
                    <p class="pe-2 m-0">
                        {{ new Date(new Date(note.time)).getHours() }}:{{
                            new Date(new Date(note.time)).getMinutes()
                        }}:{{ new Date(new Date(note.time)).getSeconds() }}
                    </p>
                    <button @click="deleteNote(note.id)" class="btn btn-danger">Eliminar</button>
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>
textarea:focus {
    outline: #0d6efd;
}
[type='submit'] {
    width: 100%;
}
</style>
