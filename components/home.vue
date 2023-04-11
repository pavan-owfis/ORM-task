<template>
  <div class="flex gap-52">
    <div>
      <div>
        <button
          type="button"
          class="rounded bg-indigo-600 px-2 py-2 text-sm ml-3 font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
          @click="isAdd = true"
        >
          Add details to timeline
        </button>
      </div>
      <h2 class="mb-[16px] font-[600] text-[21px]">Your Timeline</h2>

      <div class="flow-root ml-2">
        <ul role="list" class="-mb-8">
          <li v-for="(data, index) in ProfileData" :key="index">
            <div class="relative pb-8">
              <span
                class="absolute top-5 left-5 -ml-px h-full w-0.5 bg-gray-200"
                v-if="ProfileData.length != index + 1"
              />

              <div class="flex">
                <div class="relative px-1">
                  <div
                    class="flex h-8 w-8 items-center justify-center rounded-full bg-[#f7ecff] ring-8 ring-white"
                  >
                    <img
                      src="data:image/jpeg;base64,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"
                      class="h-[15px]"
                    />
                  </div>
                </div>

                <!-- i did a certification course during 2022 to 2023 on the technology java -->

                <div class="pl-[11px]">
                  <div
                    class="flex flex-wrap text-[16px] text-gray-700 font-[600]"
                    v-if="
                      data.start_month ||
                      data.start_month == 0 ||
                      data.start_year ||
                      data.end_month ||
                      data.end_year
                    "
                  >
                    <p class="px-1 text-[16px] text-gray-500">
                      I did a certification course during
                    </p>

                    <span
                      v-if="data.start_month || data.start_month == 0"
                      class=""
                      >{{ data.start_month }}-</span
                    >

                    <span v-if="data.start_year">{{ data.start_year }}</span>

                    <span
                      v-if="
                        (data.start_month || data.start_year) &&
                        (data.end_month || data.end_year)
                      "
                      class="px-2"
                      >to</span
                    >

                    <span v-if="data.end_month">{{ data.end_month }}-</span>

                    <span v-if="data.end_year">{{ data.end_year }}</span>

                    <span v-else class="pl-2"> to Present</span>
                  </div>

                  <h4 class="text-[16px]">
                    <span class="px-1 text-[16px] text-gray-500 font-[500]"
                      >on</span
                    >

                    <span
                      class="first-letter:capitalize px-1 text-[16px] text-gray-500 font-[500]"
                      ><span class="text-[16px] text-gray-700 font-[600]">{{
                        data.title
                      }}</span>

                      technology and get certified, <br />for more informaton
                      click on
                    </span>
                  </h4>
                  <p
                    class="text-[15px] text-slate-600 font-[500]"
                    v-if="data.url"
                  >
                    <a :href="data.url" target="_blank">{{ data.url }}</a>
                  </p>
                  <p
                    class="text-slate-600 font-[500] text-[16px] mb-0 leading-1"
                    v-if="data.description"
                  >
                    {{ data.description }}
                  </p>
                  <div class="flex gap-2">
                    <div>
                      <svg
                        xmlns="http://www.w3.org/2000/svg"
                        viewBox="0 0 20 20"
                        fill="currentColor"
                        class="w-5 h-5"
                        @click="editData(data)"
                      >
                        <path
                          d="M5.433 13.917l1.262-3.155A4 4 0 017.58 9.42l6.92-6.918a2.121 2.121 0 013 3l-6.92 6.918c-.383.383-.84.685-1.343.886l-3.154 1.262a.5.5 0 01-.65-.65z"
                        />
                        <path
                          d="M3.5 5.75c0-.69.56-1.25 1.25-1.25H10A.75.75 0 0010 3H4.75A2.75 2.75 0 002 5.75v9.5A2.75 2.75 0 004.75 18h9.5A2.75 2.75 0 0017 15.25V10a.75.75 0 00-1.5 0v5.25c0 .69-.56 1.25-1.25 1.25h-9.5c-.69 0-1.25-.56-1.25-1.25v-9.5z"
                        />
                      </svg>
                    </div>
                    <div>
                      <svg
                        xmlns="http://www.w3.org/2000/svg"
                        viewBox="0 0 20 20"
                        fill="currentColor"
                        class="w-5 h-5"
                        @click="deleteItem(index)"
                      >
                        <path
                          fill-rule="evenodd"
                          d="M8.75 1A2.75 2.75 0 006 3.75v.443c-.795.077-1.584.176-2.365.298a.75.75 0 10.23 1.482l.149-.022.841 10.518A2.75 2.75 0 007.596 19h4.807a2.75 2.75 0 002.742-2.53l.841-10.52.149.023a.75.75 0 00.23-1.482A41.03 41.03 0 0014 4.193V3.75A2.75 2.75 0 0011.25 1h-2.5zM10 4c.84 0 1.673.025 2.5.075V3.75c0-.69-.56-1.25-1.25-1.25h-2.5c-.69 0-1.25.56-1.25 1.25v.325C8.327 4.025 9.16 4 10 4zM8.58 7.72a.75.75 0 00-1.5.06l.3 7.5a.75.75 0 101.5-.06l-.3-7.5zm4.34.06a.75.75 0 10-1.5-.06l-.3 7.5a.75.75 0 101.5.06l.3-7.5z"
                          clip-rule="evenodd"
                        />
                      </svg>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </li>
        </ul>
      </div>
    </div>
    <div>
      <inputData @formData="formData" v-if="isAdd" />
      <edit v-if="isEdit" :editDetails="editDetails" />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";

const ProfileData: any = ref([]);
const isAdd = ref(false);
const isEdit = ref(false);
const editDetails = ref({});
// const emit = defineEmits(["editData"]);

function editData(data: any) {
  editDetails.value = data.value;
  isEdit.value = true;
}

//get the data
onMounted(async () => {
  await getProfileData();
});
const getProfileData = async () => {
  let data: any = localStorage.getItem("ProfileData");
  ProfileData.value = JSON.parse(data);
};

//post data into local storage
const formData = (data: object) => {
  ProfileData.value.unshift(data);
  localStorage.setItem("ProfileData", JSON.stringify(ProfileData.value));
  console.log("ProfileData", ProfileData.value);
  isAdd.value = false;
};

//delete data
const deleteItem = (index: number) => {
  ProfileData.value.splice(index, 1);
  localStorage.setItem("ProfileData", JSON.stringify(ProfileData.value));
};
</script>

<style scoped></style>
