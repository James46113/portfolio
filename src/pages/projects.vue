<template>
    <div class="home">
        <projectCard
            v-for="project in allProjects"
            :title="project.title"
            :date="project.date"
            :image-url="project.imageUrl"
            :description="project.description"
        ></projectCard>
    </div>
</template>

<script lang="ts" setup>
import allProjectsData from "@/data/projects.json"
const allProjects = allProjectsData.data;
console.log(allProjects[0].imageUrl);
</script>

<style scoped>
.home {
    align-items: center;
    display: flex;
    flex-direction: column;
    padding: 64px;
}
</style>