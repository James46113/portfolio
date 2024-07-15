<template>
    <div class="home">
        <v-card-title class="mb-7" style="font-size: 2em;">{{ tag + " Projects" }}</v-card-title>
        <v-card-text v-if="isMobile" style="text-align: center; font-style: italic;">To view images, visit webpage on desktop</v-card-text>
        <v-btn v-if="tag !== ''" class="pa-1 mb-3" style="background-color: #206060;" @click="resetTags()">{{ tag + " |  ✕"}}</v-btn>
        <projectCard
            v-for="(project, index) in allProjectsRef"
            :title="project.title"
            :date="project.date"
            :image-url="project.imageUrl"
            :description="project.description"
            :has-img="project.hasImg"
            :tags="project.tags"
            :index="index"
            :tagClicked="tagClicked"
        />
    </div>
</template>

<script lang="js" setup>

    import allProjectsData from "@/data/projects.json"
    const allProjects = allProjectsData.data;
    const allProjectsRef = ref(allProjects);

    const tag = ref("");

    const tagClicked = (tagClick) => {
        tag.value = tagClick;
        allProjectsRef.value = allProjects.filter((project) => project.tags.includes(tag.value));
        console.log(allProjectsRef.value);
    }

    const resetTags = () => {
        tag.value = "";
        allProjectsRef.value = allProjects;
    }

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
.home {
    align-items: center;
    display: flex;
    flex-direction: column;
    padding: 64px;
}
</style>