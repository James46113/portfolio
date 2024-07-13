<template>
    <v-card-title style="font-size: 1.5em;" class="mb-n3">{{ title }}</v-card-title>
                <v-card-subtitle>{{ date }}</v-card-subtitle>
                <v-card-text class="px-1 py-0 ml-4 mt-3" v-for="tag in tags" style="bottom: 0; position: static; resize: none; width: auto; display: inline-block; background-color: #206060; border-radius: 5px;">{{ tag }}</v-card-text>
                <v-card-text v-html="description"/>
</template>

<script setup lang="ts">
    defineProps ({
        title: String,
        date: String,
        tags: Array,
        description: String
    })

</script>