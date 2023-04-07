<template>
  <div>
    <div class="max-w-md mx-auto bg-white p-8 rounded-md shadow-md">
      <h1 class="text-2xl font-bold mb-6">Form</h1>
      <form>
        <div class="mb-4">
          <label for="name" class="block text-gray-700 text-sm font-bold mb-2"
            >DNS</label
          >
          <input
            type="text"
            id="name"
            name="name"
            placeholder="Enter DNS"
            class="w-full px-4 py-2 rounded-md border border-gray-300 focus:border-blue-500 focus:outline-none transition duration-300"
            v-model="name"
          />
        </div>
        <div class="relative mb-4">
          <label
            for="protocol"
            class="block text-gray-700 text-sm font-bold mb-2"
            required
            >Protocol</label
          >
          <div class="relative inline-block w-full">
            <select
              id="protocol"
              name="protocol"
              class="w-full appearance-none px-4 py-2 rounded-md border border-gray-300 focus:border-blue-500 focus:outline-none transition duration-300"
            >
              <option value="https">https</option>
              <option value="http">http</option>
              <option value="ftp">ftp</option>
            </select>
            <span
              class="absolute inset-y-0 right-0 flex items-center px-2 text-gray-500 pointer-events-none"
            >
              <svg class="h-4 w-4 fill-current" viewBox="0 0 20 20">
                <path d="M7 7l3-3 3 3m0 6l-3 3-3-3"></path>
              </svg>
            </span>
          </div>
        </div>
        <div class="mb-4">
          <label for="dns" class="block text-gray-700 text-sm font-bold mb-2"
            >User Domain</label
          >
          <input
            type="text"
            id="dns"
            name="dns"
            placeholder="Enter domain address"
            pattern="^(?=.{1,253})(?:(?!-)[A-Za-z0-9-]{1,63}(?<!-)\.?)+[A-Za-z]{2,63}\.com$"
            class="w-full px-4 py-2 rounded-md border border-gray-300 focus:border-blue-500 focus:outline-none transition duration-300"
            required
            v-model="dnsDomain"
          />
        </div>
        <div class="flex justify-end">
          <button
            type="submit"
            class="bg-blue-500 text-white px-4 py-2 rounded-md hover:bg-blue-600 transition duration-300"
            @click.prevent="addDetails"
          >
            Submit
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script setup>
let name = ref("");
let dnsDomain = ref("");

const emit = defineEmits(["addDns"]);
function addDetails() {
  console.log("Name", name.value, dns.value);
  emit("addDns", { dnsName: name.value, dnsUrl: dnsDomain.value });
  name.value = "";
  dnsDomain.value = "";
}
</script>

<style scoped></style>
