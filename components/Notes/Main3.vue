<template>
  <div class="flex gap-5 mt-8">
    <div>
      <NotesList3
        @addNote="addNotesButton"
        :getData="getData"
        @deleteCard="deleteCard"
        @editCard="editCard"
      />
    </div>
    <div>
      <NotesAdd3 v-if="type == 'add'" @notes="addNotes" />
      <Notesput v-else :inputData="inputData" @editedValue="editedValue" />
    </div>
  </div>
</template>

<script setup lang="ts">
// Import ref
import { ref } from "vue";
const isAdding: any = ref(false);
const getData = ref<object[]>([]);
const type = ref("add");

const inputData = ref({
  projectID: "",
  notes: "",
});

//Getting calls as props
const props = defineProps({
  post: { type: String, default: "" },
  get: { type: String, default: "" },
  put: { type: String, default: "" },
  deleteUrl: { type: String, default: "" },
});

function addNotesButton() {
  isAdding.value = true;
}

//get call

const { data: items } = await useAuthLazyFetch(props.get, {});
getData.value = items.value;
//get call ends here

//post call starts here
async function addNotes(input: any) {
  console.log("input", input);
  const postoptions = {
    method: "POST",

    headers: {
      "Content-Type": "application/json",

      Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiMTgxOTY5MzU5YzQ2NDQzZGFkNGM4MjVhNmMyYzc0YTkiLCJkIjoiMTY4MDA4MCIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyNzg4MDR9.jXEWiCycMvWhNsJEH-3A05EgcM1pZqKTyr-1Lt4qsoA`,
    },

    body: {
      entity_id: "string",
      project_id: input.projectId,
      note: input.notes,
      entity: "CONTACTS",
    },
  };

  const { data: items } = await useAuthLazyFetchPost(
    "https://v1-orm-lib.mars.hipso.cc/api/notes/CONTACTS/1400",
    postoptions
  );
  getData.value.unshift(items);

  //for closing sidebar
  isAdding.value = false;
}
//post call ends here

//Edit Call starts here
async function editedValue(edited: any) {
  let body = edited;
  await useAuthLazyFetchPut(`${props.put}/${data.uid}`, {
    body: JSON.stringify(body),
  });
  const { data: response } = await useAuthLazyFetch("", {});
}
//Edit Call ends here

//Delete call starts here
async function deleteCard(data: object) {
  await useAuthLazyFetchDelete(`${props.deleteUrl}/${data.uid}`, {});
  const { data: response } = await useAuthLazyFetch(props.get, {});
  getData.value = response.value;
}
//Delete ends starts here

function editCard(data) {
  type.value = "edit";
  inputData.value = data;
}
</script>
