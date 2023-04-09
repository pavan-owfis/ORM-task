<template>
  <div class="flex h-auto">
    <!-- Sidebar -->
    <div class="bg-indigo-100 text-black w-96 px-4 py-8">
      <h1 class="text-3xl font-bold mb-8">Sidebar</h1>
      <form class="space-y-4">
        <div>
          <label for="project-id" class="block font-medium">Project ID</label>
          <input
            type="text"
            id="project-id"
            class="w-full bg-white-200 text-black px-4 py-2 rounded focus:outline-none"
            v-model="editedValue.projectID"
          />
        </div>
        <div>
          <label for="notes" class="block font-medium">Notes</label>
          <textarea
            id="notes"
            class="w-full bg-white-200 text-black px-4 py-2 rounded focus:outline-none"
            v-model="editedValue.notes"
          ></textarea>
        </div>
        <button
          type="submit"
          class="bg-indigo-500 text-black px-4 py-2 rounded hover:bg-indigo-600"
          @click.prevent="editValue"
        >
          Save
        </button>
      </form>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
const emit = defineEmits(["editedValue"]);

const props = defineProps({
  inputData: {
    type: Object,
    default: { projectID: "", notes: "" },
  },
});

const editedValue = ref({});
editedValue.value = { ...props.inputData };

function editValue() {
  emit("editedValue", editedValue.value);
}
</script>
