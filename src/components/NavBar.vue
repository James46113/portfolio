<template>
    <v-app-bar :elevation="24" v-if="!isMobile" style="padding-left: 2vw;">
        <router-link :to="{ path: '/' }">
            <v-btn style="color:#ffffff; font-size: large;">James Caroe</v-btn>
        </router-link>
        <router-link :to="{ path: '/' }"> 
            <v-btn style="color:#ffffff" text="Home"/>
        </router-link>

        <router-link :to="{ path: '/projects' }"> 
            <v-btn style="color:#ffffff" text="Projects"/>
        </router-link>
        <a
            href="https://github.com/James46113"
            class="d-inline-block mx-2 social-link"
            title="James46113 - Github"
            rel="noopener noreferrer"
            target="_blank"
            style="position: absolute; right: 16px; color: #ffffff;"
        >
        <v-icon
          icon="mdi-github"
          size="22"
        />
      </a>
    </v-app-bar>
    
    <v-app-bar v-else>
        <v-app-bar-nav-icon @click.stop="showDrawer = !showDrawer"/>
        <v-app-bar-title>James Caroe</v-app-bar-title>
    </v-app-bar>

    <v-navigation-drawer v-model="showDrawer" temporary location="top">
        <v-spacer class="my-3"/>
        <router-link :to="{ path: '/' }" class="list-item"> 
            <v-list-item prepend-icon="mdi-home" title="Home"></v-list-item>
        </router-link>
        <router-link :to="{ path: '/projects' }" class="list-item"> 
            <v-list-item prepend-icon="mdi-view-list" title="Projects"></v-list-item>
        </router-link>
        
    </v-navigation-drawer>
</template>

<script setup lang="ts">
    import { RouterLink } from 'vue-router';

    const showDrawer = ref(false)

    const isMobile = ref(false);

    const checkIfMobile = () => {
        isMobile.value = window.matchMedia('(max-width: 768px)').matches;
    };

    onMounted(() => {
        checkIfMobile();
        window.addEventListener('resize', checkIfMobile);
    });

    onBeforeUnmount(() => {
        window.removeEventListener('resize', checkIfMobile);
    });
</script>

<style scoped>
    :deep(.list-item) {
        color: #ffffff;
        text-decoration: none !important;
    }
</style>