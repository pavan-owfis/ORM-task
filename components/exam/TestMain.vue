<template>
  <div>
    <div>
      <nav class="shadow-lg">
        <div class="flex items-center justify-between h-16">
          <!-- Vue.js Logo -->
          <div class="">
            <img
              class="h-8 w-8 text-white ml-2"
              src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=600"
              alt="Vue.js Logo"
            />
          </div>

          <!-- Add Employee Button -->
          <div class="flex items-center">
            <button
              class="bg-green-500 hover:bg-green-600 text-white mr-2 py-2 px-4 rounded-md font-semibold"
              @click="isSlideout = true"
            >
              Add Employee
            </button>
          </div>
        </div>
      </nav>
    </div>
    <div class="flex justify-between">
      <div class="sm:flex sm:items-center">
        <input
          type="text"
          class="position-relative mt-2 ml-2 mt-md-0 mb-2 d-lg-none d-block mobile-global-search"
          placeholder="Search"
        />
      </div>
      <div class="border border-gray-500 mr-5 my-3 px-3">
        <span>Login Name: Pavan </span>
      </div>
    </div>
    <div>
      <examTestList
        @editSlide="editSlide"
        @deleteSlide="deleteSlide"
        :detailsList="detailsList"
      />
    </div>

    <div>
      <examTestAdd
        v-if="isSlideout"
        @close="closeSlideout"
        @userDetails="userDetails"
      />
    </div>

    <div><examTestEdit @closeSlideout="closeSlideout" v-if="slideout" /></div>
    <div>
      <examTestDelete v-if="deleteData" @closeSlideout="closeSlideout" />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";

const isSlideout = ref(false);
const slideout = ref(false);
const deleteData = ref(false);
const detailsList = ref([]);

const closeSlideout = () => {
  isSlideout.value = false;
  slideout.value = false;
  deleteData.value = false;
};

const editSlide = () => {
  console.log("in edit---->", slideout.value);
  slideout.value = true;
};

//Delete the data
const deleteSlide = (index: number) => {
  detailsList.value.splice(index, 1);
  localStorage.setItem("formData", JSON.stringify(detailsList.value));
  deleteData.value = true;
};

//get the data
onMounted(() => {
  let userList = localStorage.getItem("AddedList");
  if (userList) {
    detailsList.value = JSON.parse(userList);
  }
});

//post the data
const userDetails = (data: object) => {
  console.log("data", data);
  detailsList.value.push(data);
  localStorage.setItem("AddedList", JSON.stringify(detailsList.value));
  isSlideout.value = false;
};
</script>
