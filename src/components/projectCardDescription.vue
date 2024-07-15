<template>
    <v-card-title style="font-size: 1.5em;" class="mb-n3">{{ title }}</v-card-title>
                <v-card-subtitle>{{ date }}</v-card-subtitle>
                <v-card-text class="px-1 py-0 ml-4 mt-3 mb-0 tags" v-for="tag in tags" @click="tagClicked!(tag)">{{ tag }}</v-card-text>
                <v-card-text class="mt-4" v-html="description"/>
</template>

<script setup lang="ts">
    defineProps ({
        title: String,
        date: String,
        tags: Array,
        description: String,
        tagClicked: Function,
    })

</script>

<style scoped>
    .tags {
        bottom: 0; 
        position: static; 
        resize: none; 
        width: auto; 
        display: inline-block; 
        background-color: #206060; 
        border-radius: 5px;
        cursor: pointer;  
        }
</style>