<template>
    <v-app-bar :elevation="4">
        <v-app-bar-nav-icon/>
        <v-app-bar-title>JY</v-app-bar-title>
        <template v-slot:append>
            <v-btn icon="mdi-heart" to="/todo"></v-btn>

            <v-btn icon="mdi-magnify" to="/"></v-btn>

            <v-btn icon="mdi-dots-vertical" to="/file"></v-btn>
        </template>
</v-app-bar>
</template>