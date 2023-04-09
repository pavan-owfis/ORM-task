<template>
  <div class="flex mt-40 border shadow-gray-400">
    <div
      class="flex flex-1 flex-col justify-center px-1 py-12 sm:px-6 lg:flex-none lg:px-20 xl:px-24"
    >
      <div class="mx-auto w-full max-w-sm lg:w-96">
        <div>
          <img
            class="h-12 w-auto"
            src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=600"
            alt="Your Company"
          />
          <h4 class="mt-6 text-3xl font-bold tracking-tight text-gray-900">
            Post your details
          </h4>
        </div>

        <div class="mt-8">
          <div class="mt-6">
            <form @submit.prevent="afterEdit" class="space-y-3">
              <div>
                <label class="block text-sm font-medium leading-6 text-gray-900"
                  >Name</label
                >
                <div class="mt-2">
                  <input
                    v-model="edited.name"
                    name="email"
                    type="text"
                    required
                    class="block w-full rounded-md border-0 py-1.5 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                  />
                </div>
              </div>

              <div>
                <label class="block text-sm font-medium leading-6 text-gray-900"
                  >Address</label
                >
                <div class="mt-2">
                  <input
                    v-model="edited.description"
                    name="email"
                    type="text"
                    required
                    class="block w-full rounded-md border-0 py-1.5 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                  />
                </div>
              </div>

              <div>
                <label class="block text-sm font-medium leading-6 text-gray-900"
                  >Description</label
                >
                <div class="mt-2">
                  <input
                    v-model="edited.address"
                    name="email"
                    type="text"
                    required
                    class="block w-full rounded-md border-0 py-5 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                  />
                </div>
              </div>

              <div>
                <button
                  type="submit"
                  class="flex w-full justify-center rounded-md bg-indigo-600 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                >
                  Add
                </button>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
    <!-- <div class="relative hidden w-0 flex-1 lg:block">
        <img
          class="absolute inset-0 h-full w-full object-cover"
          src="https://images.unsplash.com/photo-1505904267569-f02eaeb45a4c?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1908&q=80"
          alt=""
        />
      </div> -->
  </div>
</template>
<script setup lang="ts">
import { ref } from "vue";
const editedData = ref({});

const emit = defineEmits(["editedData"]);

const props = defineProps({
  edited: {
    type: Object,
    default: { name: "", adress: "", description: "" },
  },
});

editedData.value = { ...props.edited };

function afterEdit() {
  emit("editedData", editedData);
}
</script>
