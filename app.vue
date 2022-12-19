<script>
import { reactive } from "vue";
export default {
  setup() {
    const state = reactive({
      content: "<p>Start typing here..</p>",
      onChange: (value) => {
        state.content = value;
      },
    });

    const printContent = () => {
      console.log(state.content);
    };

    return { printContent, state };
  },
};
</script>

<template>
  <div class="flex flex-col w-full items-center justify-center p-4">
    <h1 class="text-2xl font-medium text-gray-700">Rich Text Editor</h1>
    <TextEditor :state="state" />
    <div class="flex flex-col items-end max-w-4xl w-full">
      <button
        @click="printContent"
        type="button"
        class="inline-flex items-center rounded-md border border-transparent bg-indigo-100 px-4 py-2 text-base font-medium text-indigo-700 hover:bg-indigo-200 focus:outline-none"
      >
        Console
      </button>
    </div>

    <div class="flex flex-col items-start max-w-4xl w-full">
      <h1 class="text-2xl pl-2 font-medium text-gray-700">Live Render</h1>
    </div>
    <div
      v-html="state.content"
      class="p-2 rounded-lg flex flex-col w-full max-w-4xl m-4 min-h-[20vh]"
    ></div>
  </div>
</template>
