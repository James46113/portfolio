<template>
    <v-card width="100vh" class="my-4">
        <v-card-title class="mb-n3">{{ title }}</v-card-title>
        <v-card-subtitle>{{ date }}</v-card-subtitle>
        <v-row class="ma-3">
            <v-col cols="5">
                <v-img :src="imageUrl"/>
            </v-col>
            <v-col>
                <v-card-text>{{ description }}</v-card-text>
            </v-col>
        </v-row>
    </v-card>
</template>

<script setup lang="ts">
    defineProps({
        title: String,
        date: String,
        imageUrl: String,
        description: String,
    });

</script>