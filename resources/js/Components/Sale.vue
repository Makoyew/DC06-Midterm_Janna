<script setup>
import { defineProps, inject } from 'vue';

const props = defineProps({
    sales: Array, // Ensure that this type matches the type of your sales prop
});

const darkTheme = inject('darkTheme');
</script>

<template>
    <div :class="darkTheme ? 'text-white' : 'text-gray-700'" class="mx-auto max-w-7xl sm:px-6 lg:px-8">
      <div :class="darkTheme ? 'bg-gray-700' : 'bg-white'" class="overflow-hidden shadow-sm sm:rounded-lg">
        <div :class="darkTheme ? 'text-white' : 'text-gray-700'" class="p-6 text-gray-900">
          <table class="min-w-full border divide-y divide-gray-200">
            <thead>
              <tr>
                <th>Date</th>
                <th>Client ID</th>
                <th>Is Credit</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="sale in sales" :key="sale.id">
                <td class="text-center">{{ sale.date }}</td>
                <td class="text-center">{{ sale.client_id }}</td>
                <td class="text-center">{{ sale.is_credit ? 'Yes' : 'No' }}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </template>

