<script>
export default {
  components: {},

  setup() {
    const content = ref();

    const printContent = () => {
      console.log(content.value);
    };

    return { printContent, content };
  },
};
</script>

<template>
  <div class="flex flex-col w-full items-center justify-center p-4">
    <TextEditor />
    <div class="flex flex-col items-end max-w-4xl w-full">
      <button
        @click="printContent"
        type="button"
        class="inline-flex items-center rounded-md border border-transparent bg-indigo-100 px-4 py-2 text-base font-medium text-indigo-700 hover:bg-indigo-200 focus:outline-none"
      >
        Print
      </button>
    </div>
  </div>
</template>
