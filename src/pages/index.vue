<template>
  <div class="home">
    <v-card-title class="mb-16" style="font-size: 2em;">James Caroe</v-card-title>
    <v-card width="50vw" v-if="!isMobile">
      <v-row>
        <v-col cols="4">
          <v-img src="@/assets/desktop.jpg"/>
        </v-col>
        <v-col>
          <v-card-text>I am a Y12 student studying at UTC OLP Sheffield. I am studying four A-Levels: computer science, maths, further maths (self taught), physics, and a cyber security EPQ.</v-card-text>
          <v-card-text>My hobbies include coding, singing, and playing the organ. A list of my coding projects can be found on my projects page - this also includes my cyber security EPQ.</v-card-text>
          <v-card-text>I have experience programming in C# and python, some experience with javascript mainly using vue.js, and have limited experience with C++ and Java</v-card-text>
        </v-col>
      </v-row>
    </v-card>
    <v-card width="90vw" v-else>
      <v-img src="@/assets/mobile.jpg"/>
      <v-card-text>I am a Y12 student studying at UTC OLP Sheffield. I am studying four A-Levels: computer science, maths, further maths (self taught), physics, and a cyber security EPQ.</v-card-text>
      <v-card-text>My hobbies include coding, singing, and playing the organ. A list of my coding projects can be found on my projects page - this also includes my cyber security EPQ.</v-card-text>
      <v-card-text>I have experience programming in C# and python, some experience with javascript mainly using vue.js, and have limited experience with C++ and Java</v-card-text>
    </v-card>
    <router-link :to="{ path: '/projects' }"><v-btn class="mt-9">My Projects</v-btn></router-link>
  </div>
</template>

<script lang="ts" setup>
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
