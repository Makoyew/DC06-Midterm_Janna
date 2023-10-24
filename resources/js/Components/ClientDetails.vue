<script setup>
import { computed, defineProps, inject } from 'vue';

const props = defineProps({
  client: Object,
  sales: Array,
});

const darkTheme = inject('darkTheme');

const totalAmount = computed(() => {
  if (props.sales) {
    return props.sales.reduce((sum, obj) => sum + (obj.amount || 0), 0);
  }
  return 0; // Provide a default value when props.sales is not defined.
});
</script>

<template>
  <div :class="{ 'bg-gray-200': !darkTheme, 'bg-gray-700': darkTheme }" class="grid w-full grid-cols-2 gap-8 p-8 overflow-hidden text-center shadow-sm sm:rounded-lg">
    <div class="mt-40">
      <h2 :class="{ 'text-gray-700': !darkTheme, 'text-white': darkTheme }" class="mb-4 text-3xl font-semibold text-gray-900 dark:text-white">
        {{ client.first_name }} {{ client.last_name }}
      </h2>
      <h3 :class="{ 'text-gray-700': !darkTheme, 'text-white': darkTheme }" class="mb-2 text-xl font-semibold text-gray-700 dark:text-gray-50">
        Client Details
      </h3>
      <div class="mb-4">
        <p :class="{ 'text-gray-700': !darkTheme, 'text-white': darkTheme }" class="text-sm font-semibold text-gray-700 dark:text-gray-50">
          Address:
        </p>
        <p :class="{ 'text-gray-700': !darkTheme, 'text-white': darkTheme }" class="text-sm font-light text-gray-700 dark:text-gray-50">
          {{ client.address }}
        </p>
      </div>
      <div class="mb-4">
        <p :class="{ 'text-gray-700': !darkTheme, 'text-white': darkTheme }" class="text-sm font-semibold text-gray-700 dark:text-gray-50">
          Phone:
        </p>
        <p :class="{ 'text-gray-700': !darkTheme, 'text-white': darkTheme }" class="text-sm font-light text-gray-700 dark:text-gray-50">
          {{ client.phone }}
        </p>
      </div>
      <div>
        <p :class="{ 'text-gray-700': !darkTheme, 'text-white': darkTheme }" class="text-sm font-semibold text-gray-700 dark:text-gray-50">
          Credit Limit:
        </p>
        <p :class="{ 'text-gray-700': !darkTheme, 'text-white': darkTheme }" class="text-sm font-light text-gray-700 dark:text-gray-50">
          {{ client.credit_limit }}
        </p>
      </div>
    </div>
    <div>
      <h3 :class="{ 'text-gray-700': !darkTheme, 'text-white': darkTheme }" class="mb-2 text-xl font-semibold text-center text-gray-700 dark:text-gray-50">
        Sales Transactions
      </h3>
      <table class="w-full border-collapse">
        <thead>
          <tr :class="{ 'text-gray-700': !darkTheme, 'text-white': darkTheme }">
            <th class="px-4 py-2 text-center">Date</th>
            <th class="px-4 py-2 text-center">Cash/Credit</th>
            <th class="px-4 py-2 text-center">Total</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="sale in sales" :key="sale.id" class="border-b border-gray-200 dark:border-gray-600">
            <td :class="{ 'text-gray-700': !darkTheme, 'text-white': darkTheme }" class="px-4 py-2 dark:text-white">{{ sale.date }}</td>
            <td :class="{ 'text-gray-700': !darkTheme, 'text-white': darkTheme }" class="px-4 py-2 dark:text-white">{{ sale.is_credit ? 'Credit' : 'Cash' }}</td>
            <td :class="{ 'text-gray-700': !darkTheme, 'text-white': darkTheme }" class="px-4 py-2 dark:text-white">{{ sale.amount }}</td>
          </tr>
          <tr>
            <td :class="{ 'text-gray-700': !darkTheme, 'text-white': darkTheme }" colspan="2" class="px-4 py-2 font-semibold text-right">Sum:</td>
            <td :class="{ 'text-gray-700': !darkTheme, 'text-white': darkTheme }" class="px-4 py-2 text-xl font-semibold text-center">{{ totalAmount }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
