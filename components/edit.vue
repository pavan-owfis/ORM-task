<template>
  <div>
    <div
      class="max-w-md mx-auto bg-white shadow-md rounded-md p-6"
      v-if="!isSubmitted"
    >
      <h2 class="text-2xl font-semibold mb-4">Form</h2>
      <form @submit.prevent="submitForm">
        <div class="grid grid-cols-2 gap-4">
          <div>
            <label
              for="start_month"
              class="block text-sm font-medium text-gray-700"
              >Start Month</label
            >
            <input
              v-model="editDetails.start_month"
              id="start_month"
              type="text"
              class="mt-1 px-3 py-2 w-full border-gray-300 focus:outline-none focus:border-blue-500 rounded-md"
            />
          </div>
          <div>
            <label
              for="end_month"
              class="block text-sm font-medium text-gray-700"
              >End Month</label
            >
            <input
              v-model="editDetails.end_month"
              id="end_month"
              type="text"
              class="mt-1 px-3 py-2 w-full border-gray-300 focus:outline-none focus:border-blue-500 rounded-md"
            />
          </div>
          <div>
            <label
              for="start_year"
              class="block text-sm font-medium text-gray-700"
              >Start Year</label
            >
            <input
              v-model="editDetails.start_year"
              id="start_year"
              type="text"
              class="mt-1 px-3 py-2 w-full border-gray-300 focus:outline-none focus:border-blue-500 rounded-md"
            />
          </div>
          <div>
            <label
              for="end_year"
              class="block text-sm font-medium text-gray-700"
              >End Year</label
            >
            <input
              v-model="editDetails.end_year"
              id="end_year"
              type="text"
              class="mt-1 px-3 py-2 w-full border-gray-300 focus:outline-none focus:border-blue-500 rounded-md"
            />
          </div>
        </div>
        <div class="mt-4">
          <label for="title" class="block text-sm font-medium text-gray-700"
            >Title</label
          >
          <input
            v-model="editDetails.title"
            id="title"
            type="text"
            class="mt-1 px-3 py-2 w-full border-gray-300 focus:outline-none focus:border-blue-500 rounded-md"
          />
        </div>
        <div class="mt-4">
          <label for="url" class="block text-sm font-medium text-gray-700"
            >URL</label
          >
          <input
            v-model="editDetails.url"
            id="url"
            type="text"
            class="mt-1 px-3 py-2 w-full border-gray-300 focus:outline-none focus:border-blue-500 rounded-md"
          />
        </div>
        <div class="mt-4">
          <label
            for="description"
            class="block text-sm font-medium text-gray-700"
            >Description</label
          >
          <textarea
            v-model="editDetails.description"
            id="description"
            rows="3"
            class="mt-1 px-3 py-2 w-full border-gray-300 focus:outline-none focus:border-blue-500 rounded-md"
          ></textarea>
        </div>
        <button
          type="submit"
          class="mt-6 px-4 py-2 bg-blue-500 text-white rounded-md hover:bg-blue-600"
        >
          Submit
        </button>
      </form>
    </div>
  </div>
</template>

<script setup lang="ts">
import { defineProps } from "vue";
defineProps({
  editDetails: {
    type: Object,
  },
});
</script>
