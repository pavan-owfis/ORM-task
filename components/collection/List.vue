<template>
  <!-- <div v-for="(template, index) in templates" :key="index"> -->
  <!-- Start of templates list-->

  <!-- Emit selected template when click on template -->
  <!-- <div > -->
  <!-- Start of icon -->
  <!-- <span>
            <DocumentIcon v-if="template.type"  class="h-5 w-5 font-[500] text-gray-600 mr-2 sm:mt-[20px]"/>
         </span> -->
  <!-- End of icon -->
  <!-- <div class="ml-[50px] mt-[-20px]">
        <p class="text-b">
          {{ template.name }}
        </p>
        <p class="text-gray-600">{{ template.subject }}</p>
        <p class="text-sm text-gray-600 mb-[90px]">
          {{ preview(template.body) }}
        </p>
      </div>
    </div> -->
  <!-- End of templates list -->

  <!-- End of delete icon -->

  <div>
    <nav class="min-h-0 flex-1 overflow-y-auto" aria-label="Directory">
      <!-- <div
          class="sticky top-0 z-10 border-b border-t border-gray-200 bg-gray-50 px-6 py-1 text-sm font-medium text-gray-500"
        >
          <h3>{{ letter }}</h3>
        </div> -->
      <ul role="list" class="relative z-0 divide-y divide-gray-200">
        <li
          v-for="(template, index) in templates"
          :key="index"
          @click="emitSelectedTemplate(template)"
        >
          <div
            class="relative flex items-center space-x-3 px-6 py-5 focus-within:ring-2 focus-within:ring-inset focus-within:ring-pink-500 hover:bg-gray-50"
          >
            <div class="min-w-0 flex-1">
              <a href="#" class="focus:outline-none">
                <span class="absolute inset-0" aria-hidden="true" />
                <p class="text-sm font-medium text-gray-900">
                  {{ template.name }}
                </p>
                <p class="truncate text-sm text-gray-500">
                  {{ template.subject }}
                </p>
                <p class="truncate text-sm text-gray-500">
                  {{ template.body }}
                </p>
              </a>
            </div>
            <TrashIcon
              class="h-5 w-5 text-gray-600 ml-[15rem] mt-[-120px]"
              @click="() => emit('delete', template.uid)"
            />
          </div>
        </li>
      </ul>
    </nav>
  </div>
  <!-- </div> -->
</template>

<script setup lang="ts">
import {
  EnvelopeIcon,
  CodeBracketIcon,
  DocumentIcon,
  TrashIcon,
} from "@heroicons/vue/24/outline";
// Define props
defineProps({
  // Take templates list as props
  templates: {
    type: Array,
    default: () => {
      return [];
    },
  },
});

// Define emits
const emit = defineEmits(["select", "delete"]);

// Emit selected template when click on template
const emitSelectedTemplate = (template: object) => {
  emit("select", template);
};

// Show preview of template body
const preview = (body: string) => {
  if (body) {
    const templateBody = body.replace(/<\/?[^>]+(>|$)/g, "").trim();
    return templateBody.slice(0, 50);
  }
};
</script>
<style scoped></style>
