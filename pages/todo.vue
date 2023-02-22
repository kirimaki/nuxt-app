<template>
    <v-container class="todo-section">
        <v-card v-for="todo in todos" :key="todo">
            <v-card-title>{{ todo.title }}</v-card-title>
            <v-card-text>{{ todo.content }}</v-card-text>
        </v-card>
    </v-container>
</template>

<script setup langs="ts">
import data from "~~/assets/javascripts/data";

const todos = ref([...data]);
</script>

<style lang="scss">
.todo-section {
    width: 600px;
}
</style>