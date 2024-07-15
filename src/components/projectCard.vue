<template>
    <v-card width="70vw" class="my-4" v-if="!isMobile">
        <v-row>
            <v-col cols="4" v-if="hasImg && index!%2 == 0">
                <v-img :src="imageUrl"/>
            </v-col>
            <v-col v-if="index!%2 == 0" :cols="hasImg ? 8 : false">
                <project-card-description :title="title" :date="date" :tags="tags" :description="description" :tagClicked="tagClicked"/>
            </v-col>
            <v-col v-if="index!%2 == 1" :cols="hasImg ? 8 : false">
                <project-card-description :title="title" :date="date" :tags="tags" :description="description" :tagClicked="tagClicked"/>
            </v-col>
            <v-col cols="4" v-if="hasImg && index!%2 == 1">
                <v-img :src="imageUrl"/>
            </v-col>
        </v-row>
    </v-card>
    <v-card width="90vw" class="my-4" v-else>
        <project-card-description :title="title" :date="date" :tags="tags" :description="description" :tagClicked="tagClicked"/>
    </v-card>
</template>

<script setup lang="ts">
    defineProps({
        title: String,
        date: String,
        imageUrl: String,
        description: String,
        hasImg: Boolean,
        tags: Array,
        index: Number,
        tagClicked: Function,
    });

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
    
</style>