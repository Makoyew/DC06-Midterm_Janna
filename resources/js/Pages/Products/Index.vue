<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, Link, usePage } from '@inertiajs/vue3';
import Product from '@/Components/Product.vue';

const page = usePage();

const { products } = defineProps(['products']);
</script>

<template>
  <Head title="Products" />

  <AuthenticatedLayout>
    <div class="grid justify-center grid-cols-4 mt-5">
        <div class="flex justify-center col-span-4">
          <Link v-if="$page.props.auth.user.permissions.includes('create')" :href="route('product.create')" class="px-4 py-3 text-sm text-white bg-gray-500 rounded-md">
            Add Product
          </Link>
        </div>
      </div>
    <div class="py-12">
      <div class="grid grid-cols-4 gap-4">
        <Product
          v-for="product in products"
          :key="product.id"
          :product="product"
          class="rounded-md shadow-lg cursor-pointer"
        />
      </div>
    </div>
  </AuthenticatedLayout>
</template>
