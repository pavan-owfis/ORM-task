<template>
  <div class="flex">
    <div>
      <projectsAdd2
        @formData="formData"
        @addData="addData"
        v-if="type == 'add'"
      />
      <ProjectsEdit2 v-else :edited="edited" @="editedData" :key="render" />
    </div>
    <div>
      <projectsList2
        :addedData="addedData"
        @deleteCard="deleteCard"
        @editCard="editCard"
        :key="renderList"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, defineProps } from "vue";

const addedData = ref<object[]>([]);
const type = ref("add");
const render = ref(0);
const renderList = ref(0);
const edited = ref({
  name: "",
  adress: "",
  description: "",
});

const props = defineProps({
  // Get ORM calls by props from index.vue file
  post: { type: String, default: "" },
  get: { type: String, default: "" },
  put: { type: String, default: "" },
  deleteUrl: { type: String, default: "" },
});

// function addData() {
//   type.value = true;
// }

function editCard(data: any) {
  type.value = "edit";
  render.value++;
  edited.value = data;
}

//Post the data
const authHeader = {
  Authorization:
    "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiMTgxOTY5MzU5YzQ2NDQzZGFkNGM4MjVhNmMyYzc0YTkiLCJkIjoiMTY4MDA4MCIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyNzg4MDR9.jXEWiCycMvWhNsJEH-3A05EgcM1pZqKTyr-1Lt4qsoA",
};
async function formData(input: any) {
  let body = {
    name: input.name,
    property_build_area: 0,
    blocks: 0,
    units: "string",
    total_floors: 0,
    approve_status: "Active",
    description: input.description,
    address: input.address,
    avg_price: 0,
    flats_in_floor: 0,
    prefs: {
      available: "Boy",
      suited: "Students",
      allowed_non_veg: true,
      allowed_opposite_sex: true,
      allowed_any_time: true,
      allowed_visitors: true,
      allowed_drinking: true,
    },
    project_id: "string",
    visit_count: 0,
  };

  const { data: items } = await useAuthLazyFetchPost(props.post, {
    method: "POST",
    headers: authHeader,
    body: body,
  });
  addedData.value.unshift(body);
}
//post call ends here

//get call starts here
const { data: items } = await useAuthLazyFetch(props.get, {});

addedData.value = items.value;
//get call ends here

//put call start here
async function editedData(data: any) {
  let body = data;
  const { data: edited } = await useAuthLazyFetchPost(
    `${props.post}/${data.uid}`,
    {
      body: body,
    }
  );

  addedData.value = edited.value;
  renderList.value++;
}

//put call ends here

//Delete start here
async function deleteCard(data) {
  await useAuthLazyFetchDelete(`${props.deleteUrl}/${data.uid}`, {});
  const { data: response } = await useAuthLazyFetch(props.get, {});
  addedData.value = response.value;
}
//Delete end here
</script>
