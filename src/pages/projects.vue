<template>
    <div class="home">
        <v-card-title class="mb-7" style="font-size: 2em;">Projects</v-card-title>
        <projectCard
            v-for="(project, index) in allProjects"
            :title="project.title"
            :date="project.date"
            :image-url="project.imageUrl"
            :description="project.description"
            :has-img="project.hasImg"
            :tags="project.tags"
            :index="index"
        />
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