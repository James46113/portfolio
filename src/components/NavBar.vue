<script setup lang="ts">
import { RouterLink } from 'vue-router';
</script>

<template>
    <v-app-bar>
        <router-link :to="{ path: '/' }">
            <v-btn class="mx-6" style="color:#ffffff; font-size: large;">James Caroe</v-btn>
        </router-link>
        <router-link :to="{ path: '/' }"> 
            <v-btn style="color:#ffffff" text="Home"/>
        </router-link>

        <router-link :to="{ path: '/projects' }"> 
            <v-btn style="color:#ffffff" text="Projects"/>
        </router-link>
    </v-app-bar>
</template>
