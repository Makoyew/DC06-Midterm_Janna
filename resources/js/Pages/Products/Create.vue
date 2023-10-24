<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import ProductForm from '@/Components/ProductForm.vue';
</script>

<template>
    <Head title="Add New Product" />
    <AuthenticatedLayout>
      <div class="py-12">
        <div class="max-w-2xl mx-auto sm:px-6 lg:px-8">
          <ProductForm />
        </div>
      </div>
    </AuthenticatedLayout>
  </template>
