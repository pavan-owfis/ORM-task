<template>
  <div class="flex justify-center items-center h-screen bg-gray-100">
    <div class="grid grid-cols-2 gap-8">
      <div>
        <button
          class="bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded ml-32"
          @click="buttonclick"
        >
          Click me
        </button>
        <collectionList :formInputs="formInputs" />
      </div>
      <div v-if="button">
        <collectionAdd @addDns="inputData" />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
const button = ref(false);
const formInputs = ref<object[]>([]);

function buttonclick() {
  button.value = true;
}

//Get the data
const { data: items } = await useAuthLazyFetch(
  "https://v1-orm-lib.mars.hipso.cc/dns/search/by-dns/www.example.com?type=DOMAIN&offset=0&limit=100&sort_column=id&sort_direction=desc",
  {}
);
formInputs.value = items.value;

//Post the data
async function inputData(input: object) {
  let body = {
    project_id: "string",
    dns: input.dnsName,
    type: "DOMAIN",
    user_domain: input.dnsUrl,
    shortener: "string",
    ttl: "FIVE_MINUTES",
    dns_type: "CNAME",
  };
  const { data: items, pending } = await useAuthLazyFetchPost(
    "https://v1-orm-lib.mars.hipso.cc/dns/",
    {
      body: JSON.stringify(body),
    }
  );
  console.log("data", items, pending);
  formInputs.value.unshift(input);
}
</script>

<style scoped></style>
