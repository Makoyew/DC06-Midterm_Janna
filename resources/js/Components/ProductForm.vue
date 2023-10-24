<script>
import TextInput from '@/Components/TextInput.vue';
import InputLabel from '@/Components/InputLabel.vue';

export default {
  components: {
    TextInput,
    InputLabel,
  },
  methods: {
    cancel() {
      if (confirm('Are you sure you want to cancel?')) {
        window.location.href = '/product';
      }
    },
  }
}
</script>

<template>
  <div class="bg-white shadow-sm sm:rounded-lg">
    <div class="p-6">
      <h2 class="text-2xl font-semibold text-gray-800">Product Details</h2>

      <div class="grid grid-cols-2 gap-6 mt-6">
        <div>
          <InputLabel for="product" value="Product Name" />
          <TextInput type="text" class="w-full" id="product" />
        </div>

        <div>
          <InputLabel for="brand" value="Brand" />
          <TextInput type="text" class="w-full" id="brand" />
        </div>

        <div class="col-span-2">
          <InputLabel for="description" value="Description" />
          <textarea
            id="description"
            class="w-full mt-2 border rounded-lg"
          ></textarea>
        </div>

        <div>
          <InputLabel for="retail_price" value="Retail Price" />
          <TextInput type="number" class="w-full" id="retail_price" />
        </div>

        <div>
          <InputLabel for="qty_stock" value="Quantity in Stock" />
          <TextInput type="number" class="w-full" id="qty_stock" />
        </div>

        <div class="col-span-2">
          <InputLabel for="category" value="Category" />
          <select id="category" class="w-full border rounded-lg">
            <option value="" selected>Select a Category</option>
            <!-- Add category options here -->
          </select>
        </div>

        <div class="col-span-2">
          <InputLabel for="image" value="Product Image" />
          <input type="file" class="w-full border rounded-lg" id="image" />
        </div>
      </div>

      <div class="flex justify-end mt-6 space-x-4">
        <button @click="cancel" class="px-4 py-2 text-gray-800 border rounded-md hover:bg-gray-100">
          Cancel
        </button>
        <button class="px-4 py-2 text-white bg-indigo-600 rounded-md hover:bg-indigo-700">
          Save Product
        </button>
      </div>
    </div>
  </div>
</template>
