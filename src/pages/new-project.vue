<template>
    <div class="home">
        <v-card-title style="font-size: 2em;">New Project</v-card-title>
        <v-card width="50vw" class="pa-5 mt-4">
            <v-text-field clearable v-model="title" label="Title" variant="underlined"/>
            <v-text-field clearable v-model="date" label="Date" variant="underlined"/>
            <v-textarea   clearable v-model="description" label="Description" variant="underlined"/>
            <v-text-field clearable v-model="tags" label="Tags" variant="underlined"/>
            <v-file-input clearable v-model="image" label="Image"/>
            <v-card-actions>
            <v-btn width="50vw" @click="createJSON">Create</v-btn>
            </v-card-actions>
        </v-card>
        <v-dialog width="20vw" v-model="showDialog">
            <v-card>
                <v-card-title>Copied to Clipboard</v-card-title>
                <v-btn @click="showDialog = false">Close</v-btn>
            </v-card>
        </v-dialog>
    </div>
</template>

<script setup>
const title = ref("")
const date = ref("")
const description = ref("")
const tags = ref("")
const image = ref("")
const imageBase64 = ref("")
const showDialog = ref(false)
const output = ref({})


const createJSON = () => {
    if (image.value !== ""){
        const reader = new FileReader();
        reader.readAsDataURL(image.value);
        const tags2 = tags.value;
        reader.onload = () => {
            imageBase64.value = reader.result;
            output.value = imageBase64.value;
            showDialog.value = true;
            copyToClipboard(
                JSON.stringify({
                    title: title.value,
                    date: date.value,
                    description: description.value.replaceAll("\n", "<br/>").replaceAll("<a", "<a target='_blank' rel='noopener noreferrer'"),
                    tags: tags2.split(", "),
                    imageUrl: imageBase64.value,
                    hasImg: true
                }, null, "\t").replaceAll("],\n\t\"", "],\n\n\t\"") + ","
            )
        }
    }
    else {
        showDialog.value = true;
        copyToClipboard(
                JSON.stringify({
                    title: title.value,
                    date: date.value,
                    description: description.value.replaceAll("\n", "<br/>").replaceAll("<a", "<a target='_blank' rel='noopener noreferrer'"),
                    tags: tags.value.split(", "),
                    imageUrl: "",
                    hasImg: false
                }, null, "\t").replaceAll("],\n\t\"", "],\n\n\t\"") + ","
            )
    }
    
    title.value = "";
    date.value = "";
    description.value = "";
    tags.value = ""; 
    image.value = "";
    imageBase64.value = "";
    output.value = {};
}

const copyToClipboard = (text) => {
    const copyText = document.createElement('textarea');
    copyText.value = text;
    copyText.select();
    copyText.setSelectionRange(0, 99999);
    navigator.clipboard.writeText(copyText.value);
}

</script>

<style scoped>
.home {
    align-items: center;
    display: flex;
    flex-direction: column;
    padding: 64px;
}
v-dialog {
    position: absolute;
    bottom: 0;
    right: 0;
}
</style>
