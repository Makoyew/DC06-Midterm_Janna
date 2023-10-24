<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/vue3';
import { defineProps } from 'vue';
import User from '@/Components/User.vue'

const { users } = defineProps(['users']);
</script>

<template>
    <div>
      <Head title="Users" />
      <AuthenticatedLayout>
        <div class="flex justify-center mx-auto mt-5">
          <div class="w-full sm:w-2/3">
            <table class="w-full border border-collapse">
              <thead>
                <tr class="bg-gray-200">
                  <th class="px-4 py-2 text-left">ID</th>
                  <th class="px-4 py-2 text-left">Name</th>
                  <th class="px-4 py-2 text-left">Email</th>
                </tr>
              </thead>
              <tbody>
                <User
                  v-for="user in users"
                  :key="user.id"
                  :user="user"
                />
              </tbody>
            </table>
          </div>
        </div>
      </AuthenticatedLayout>
    </div>
  </template>
