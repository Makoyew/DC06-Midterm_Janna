<script setup>
import { defineProps, inject } from 'vue';

const { user } = defineProps(['user']);
const darkTheme = inject('darkTheme');
</script>

<template>
    <tr>
      <td :class="darkTheme ? 'text-white' : 'text-gray-700'" class="px-4 py-2 text-left">{{ user.id }}</td>
      <td :class="darkTheme ? 'text-white' : 'text-gray-700'" class="px-4 py-2 text-left">{{ user.name }}</td>
      <td :class="darkTheme ? 'text-white' : 'text-gray-700'" class="px-4 py-2 text-left">{{ user.email }}</td>
    </tr>
  </template>

