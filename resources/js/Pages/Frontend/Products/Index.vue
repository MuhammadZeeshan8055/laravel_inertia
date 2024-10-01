<template>

    <Head title="Product" />
    <FrontendLayout>
        <!-- Flash Message -->
        <div v-if="$page.props.flash.message" class="alert alert-success">
            {{ $page.props.flash.message }}
        </div>
        <div class="mt-4 mx-4">
            <div class="flex justify-between">
                <Link :href="route('products.create')" class="px-2 oy-1 text-sm bg-blue-300 text-dark me-2 rounded inline-block">
                    Add Student
                </Link>
            </div>
            <table class="w-full bg-white border border-gray-200 shadow">
                <thead>
                    <tr>
                        <th class="py-2 px-4 text-left border">Id</th>
                        <th class="py-2 px-4 text-left border">Name</th>
                        <th class="py-2 px-4 text-left border">Price</th>
                        <th class="py-2 px-4 text-left border">Action</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(item, index) in products" :key="index">
                        <td class="py-2 px-4 border">{{item.id}}</td>
                        <td class="py-2 px-4 border">{{item.name}}</td>
                        <td class="py-2 px-4 border">{{item.price}}</td>
                        <td>
                           
                            <Link :href="route('products.edit', item.id)" class="px-2 oy-1 text-sm bg-blue-300 text-dark me-2 rounded inline-block">
                                Edit
                            </Link>
                           <button v-on:click="deleteProduct(item.id)" class="px-2 oy-1 text-sm bg-blue-300 text-dark me-2 rounded inline-block">
                                Delete
                           </button>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </FrontendLayout>
</template>
<script setup>
import FrontendLayout from '@/Layouts/Frontend/FrontendLayout.vue';
import { Head, useForm } from '@inertiajs/vue3';
import { Link } from '@inertiajs/vue3';

defineProps({
    products:Array
});

const form=useForm({});

const deleteProduct = (id) => {
    
    if(confirm('Are you sure want to delete this data?')){
        form.delete(route('products.destroy',id))
    }
    
};

</script>