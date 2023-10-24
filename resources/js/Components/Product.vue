<script setup>
import { defineProps, inject } from 'vue';

const { product } = defineProps(['product']);
const darkTheme = inject('darkTheme');
</script>

<template>
    <div v-if="product" :class="{ 'bg-gray-200': !darkTheme, 'bg-gray-700': darkTheme }" class="rounded-md shadow-md ">
      <div class="h-[150px] overflow-hidden">
        <img class="object-cover w-full h-full" :src="product.thumbnail" alt="">
      </div>
      <div  class="p-4">
        <h1 :class="darkTheme ? 'text-white' : 'text-gray-700'" class="text-lg font-semibold text-gray-700">{{ product.name }}</h1>
        <span class="px-4 py-1.5 mt-3 text-xs font-semibold bg-gray-50 tracking-wide uppercase text-gray-500">{{ product.category }}</span>
        <p :class="darkTheme ? 'text-white' : 'text-gray-700'" class="font-semibold text-gray-600 text-md">₱ {{ product.retail_price }}</p>
      </div>
    </div>
  </template>


