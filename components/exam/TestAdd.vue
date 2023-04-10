<template>
  <TransitionRoot as="template" :show="open">
    <Dialog as="div" class="relative z-10" @close="open = false">
      <div class="fixed inset-0" />

      <div class="fixed inset-0 overflow-hidden">
        <div class="absolute inset-0 overflow-hidden">
          <div
            class="pointer-events-none fixed inset-y-0 right-0 flex max-w-full pl-10"
          >
            <TransitionChild
              as="template"
              enter="transform transition ease-in-out duration-500 sm:duration-700"
              enter-from="translate-x-full"
              enter-to="translate-x-0"
              leave="transform transition ease-in-out duration-500 sm:duration-700"
              leave-from="translate-x-0"
              leave-to="translate-x-full"
            >
              <DialogPanel class="pointer-events-auto w-screen max-w-md">
                <div
                  class="flex h-full flex-col overflow-y-scroll bg-white py-6 shadow-xl"
                >
                  <div class="px-4 sm:px-6">
                    <div class="flex items-start justify-between">
                      <DialogTitle
                        class="text-base font-semibold leading-6 text-gray-900"
                        >Add Details</DialogTitle
                      >
                      <div class="ml-3 flex h-7 items-center">
                        <button
                          type="button"
                          class="rounded-md bg-white text-gray-400 hover:text-gray-500 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2"
                          @click="$emit('close')"
                        >
                          <span class="sr-only">Close panel</span>
                          <XMarkIcon class="h-6 w-6" aria-hidden="true" />
                        </button>
                      </div>
                    </div>
                  </div>
                  <div class="relative mt-6 flex-1 px-4 sm:px-6">
                    <!-- Slide-over panel -->

                    <!-- Content -->
                    <div class="px-4 py-4">
                      <!-- Name input -->
                      <div class="mb-4">
                        <label
                          for="name"
                          class="block text-gray-700 font-semibold mb-1"
                          >Name</label
                        >
                        <input
                          id="name"
                          type="text"
                          class="w-full border-gray-300 rounded-md px-3 py-2 focus:outline-2 focus:border-blue-500"
                          v-model="userDetails.name"
                        />
                      </div>

                      <!-- Age input -->
                      <div class="mb-4">
                        <label
                          for="age"
                          class="block text-gray-700 font-semibold mb-1"
                          >Age</label
                        >
                        <input
                          id="age"
                          type="number"
                          class="w-full border-gray-300 rounded-md px-3 py-2 focus:outline-2 focus:border-blue-500"
                          v-model="userDetails.age"
                        />
                      </div>

                      <!-- Gender dropdown -->
                      <div class="mb-4">
                        <label
                          for="gender"
                          class="block text-gray-700 font-semibold mb-1"
                          >Gender</label
                        >
                        <select
                          id="gender"
                          class="w-full border-gray-300 rounded-md px-3 py-2 focus:outline-none focus:border-blue-500"
                          v-model="userDetails.gender"
                        >
                          <option value="">Select Gender</option>
                          <option value="male">Male</option>
                          <option value="female">Female</option>
                          <option value="other">Other</option>
                        </select>
                      </div>

                      <!-- Date of joining input -->
                      <div class="mb-4">
                        <label
                          for="dateOfJoining"
                          class="block text-gray-700 font-semibold mb-1"
                          >Date of Joining</label
                        >
                        <input
                          id="dateOfJoining"
                          type="date"
                          class="w-full border-gray-300 rounded-md px-3 py-2 focus:outline-none focus:border-blue-500"
                          v-model="userDetails.doj"
                        />
                      </div>

                      <!-- Designation dropdown -->
                      <div class="mb-4">
                        <label
                          for="designation"
                          class="block text-gray-700 font-semibold mb-1"
                          >Designation</label
                        >
                        <select
                          id="designation"
                          class="w-full border-gray-300 rounded-md px-3 py-2 focus:outline-none focus:border-blue-500"
                          v-model="userDetails.designation"
                        >
                          <option value="">Select Designation</option>
                          <option value="manager">Manager</option>
                          <option value="developer">Developer</option>
                          <option value="designer">Designer</option>
                        </select>
                      </div>

                      <!-- Actions -->
                      <div class="flex justify-end">
                        <button
                          class="bg-blue-500 hover:bg-blue-600 text-white rounded-md px-4 py-2 font-semibold"
                          @click="addDeatails"
                        >
                          Save
                        </button>
                        <button
                          class="bg-gray-300 hover:bg-gray-400 text-gray-700 rounded-md px-4 py-2 ml-2 font-semibold"
                        >
                          Cancel
                        </button>
                      </div>
                    </div>
                  </div>
                </div>
              </DialogPanel>
            </TransitionChild>
          </div>
        </div>
      </div>
    </Dialog>
  </TransitionRoot>
</template>

<script setup lang="ts">
import { ref } from "vue";
import {
  Dialog,
  DialogPanel,
  DialogTitle,
  TransitionChild,
  TransitionRoot,
} from "@headlessui/vue";
import { XMarkIcon } from "@heroicons/vue/24/outline";

const open = ref(true);
const emit = defineEmits(["close", "userDetails"]);
const userDetails = ref({
  name: "",
  age: "",
  gender: "",
  doj: "",
  designation: "",
});

const addDeatails = () => {
  emit("userDetails", userDetails);
};
</script>
