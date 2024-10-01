<template>
    <FrontendLayout>
        <h1>This is {{ title }} page</h1>
    </FrontendLayout>
</template>
<script setup>
import FrontendLayout from '@/Layouts/Frontend/FrontendLayout.vue';

defineProps({
    title:String
});
</script>