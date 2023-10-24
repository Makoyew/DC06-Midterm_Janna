<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import ClientDetails from '@/Components/ClientDetails.vue'; // Import the ClientDetails component

const props = defineProps({
  client: Object,
  sales: Array,
});
</script>

<template>
    <AuthenticatedLayout>
      <div class="flex items-center justify-center py-8 mx-auto max-w-7xl sm:px-6 lg:px-4">
        <ClientDetails :client="client" :sales="sales" />
      </div>
    </AuthenticatedLayout>
  </template>
