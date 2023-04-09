<template>
  <div class="flex h-auto">
    <!-- Sidebar -->
    <div class="bg-indigo-100 text-black w-96 px-4 py-8">
      <h3 class="text-2xl font-bold mb-8">Add your notes</h3>
      <form class="space-y-4">
        <div>
          <label for="project-id" class="block font-medium">Project ID</label>
          <input
            type="text"
            id="project-id"
            class="w-full bg-white-200 text-black px-4 py-2 rounded focus:outline-none"
            v-model="projectId"
          />
        </div>
        <div>
          <label for="notes" class="block font-medium">Notes</label>
          <textarea
            id="notes"
            class="w-full bg-white-200 text-black px-4 py-2 rounded focus:outline-none"
            v-model="notes"
          ></textarea>
        </div>
        <button
          type="submit"
          class="bg-indigo-500 text-black px-4 py-2 rounded hover:bg-indigo-600"
          @click.prevent="addNotes"
        >
          Save
        </button>
      </form>
    </div>
  </div>
</template>
<script setup lang="ts">
import { ref } from "vue";

const projectId = ref("");
const notes = ref("");

const emit = defineEmits(["notes"]);

function addNotes() {
  emit("notes", { projectId, notes });
}
</script>
