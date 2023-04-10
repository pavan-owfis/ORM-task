<template>
  <div class="bg-gray-800 py-10">
    <div class="px-4 sm:px-6 lg:px-8">
      <div class="mt-8 flow-root">
        <div class="-mx-4 -my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
          <div
            class="inline-block min-w-full py-2 align-middle sm:px-6 lg:px-8"
          >
            <table class="min-w-full divide-y divide-gray-700">
              <thead>
                <tr>
                  <!-- <th
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-white sm:pl-0"
                  >
                    S.No
                  </th> -->
                  <th
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-white sm:pl-0"
                  >
                    Name
                  </th>
                  <th
                    scope="col"
                    class="px-3 py-3.5 text-left text-sm font-semibold text-white"
                  >
                    Age
                  </th>
                  <th
                    scope="col"
                    class="px-3 py-3.5 text-left text-sm font-semibold text-white"
                  >
                    Gender
                  </th>
                  <th
                    scope="col"
                    class="px-3 py-3.5 text-left text-sm font-semibold text-white"
                  >
                    Date of Joining
                  </th>
                  <th
                    scope="col"
                    class="px-3 py-3.5 text-left text-sm font-semibold text-white"
                  >
                    Designation
                  </th>

                  <th scope="col" class="relative py-3.5 pl-3 pr-4 sm:pr-0">
                    <span class="sr-only">Edit</span>
                    <span class="sr-only">Delete</span>
                  </th>
                </tr>
              </thead>
              <tbody class="divide-y divide-gray-800">
                <tr v-for="(detail, index) in detailsList" :key="index">
                  <!-- <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-white sm:pl-0"
                  >
                    {{ person.sno }}
                  </td> -->
                  <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-white sm:pl-0"
                  >
                    {{ detail.name }}
                  </td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-300">
                    {{ detail.age }}
                  </td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-300">
                    {{ detail.gender }}
                  </td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-300">
                    {{ detail.doj }}
                  </td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-300">
                    {{ detail.designation }}
                  </td>

                  <td
                    class="relative whitespace-nowrap py-4 pl-3 pr-4 text-right text-sm font-medium sm:pr-0"
                  >
                    <a
                      href="#"
                      class="text-indigo-400 hover:text-indigo-300"
                      @click="emit('editSlide')"
                      >Edit</a
                    >
                  </td>

                  <td
                    class="relative whitespace-nowrap py-4 pl-3 pr-4 text-right text-sm font-medium sm:pr-0"
                  >
                    <a
                      href="#"
                      class="text-indigo-400 hover:text-indigo-300"
                      @click="emit('deleteSlide', detail, index)"
                      >Delete</a
                    >
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  detailsList: {
    type: Array,
    default: () => [],
  },
});

const emit = defineEmits(["editSlide", "deleteSlide"]);
</script>
