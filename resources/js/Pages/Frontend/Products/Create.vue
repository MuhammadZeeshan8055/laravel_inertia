<template>
    <FrontendLayout>
        <Link :href="route('products.index')">Back</Link>
        <br>
        <br>
        <form @submit.prevent="saveForm">
            <input type="text" name="name" id="name" placeholder="Enter Name" v-model="form.name">
            <br>
            <br>
            <input type="text" name="price" id="price" placeholder="Enter Price" v-model="form.price">
            <br>
            <br>
            <button type="submit" class="px-2 oy-1 text-sm bg-blue-300 text-dark me-2 rounded inline-block">Submit</button>
        </form>
    </FrontendLayout>
</template>

<script setup>
import FrontendLayout from '@/Layouts/Frontend/FrontendLayout.vue';
import { Link, useForm } from '@inertiajs/vue3';

// Use Inertia's useForm helper to create a form object
const form = useForm({
    name: '',
    price: ''
});

// Function to handle form submission
const saveForm = () => {
    // Send a POST request to the resource route using Inertia
    // form.post(route('products.store'), {
    //     onSuccess: () => {
    //         console.log("Product created successfully.");
    //     },
    //     onError: (errors) => {
    //         console.log("Error occurred:", errors);
    //     }
    // });
    const res = form.post(route('products.store'));
    if(res){
        form.reset();
    }
};
</script>
