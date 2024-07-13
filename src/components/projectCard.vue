<template>
    <v-card width="140vh" class="my-4">
        <v-row>
            <v-col cols="4" v-if="hasImg && index!%2 == 0">
                <v-img :src="imgUrl"/>
            </v-col>
            <v-col v-if="index!%2 == 0">
                <project-card-description :title="title" :date="date" :tags="tags" :description="description"/>
            </v-col>
            <v-col v-if="index!%2 == 1">
                <project-card-description :title="title" :date="date" :tags="tags" :description="description"/>
            </v-col>
            <v-col cols="4" v-if="imgUrl && index!%2 == 1">
                <v-img :src="imgUrl"/>
            </v-col>
        </v-row>
    </v-card>
</template>

<script setup lang="ts">
    const props = defineProps({
        title: String,
        date: String,
        imageUrl: String,
        description: String,
        hasImg: Boolean,
        tags: Array,
        index: Number,
    });
    const imgUrl = new URL(props.imageUrl!, import.meta.url).href;
    //const imgUrl = "/" + props.imageUrl;
</script>

<style scoped>

</style>