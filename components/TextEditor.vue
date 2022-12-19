<script>
import { useEditor, EditorContent } from "@tiptap/vue-3";
import StarterKit from "@tiptap/starter-kit";

export default {
  components: {
    EditorContent,
  },

  setup() {
    const editor = useEditor({
      content: "<p>Start typing here..</p>",
      extensions: [StarterKit],
    });

    return { editor };
  },
};
</script>

<template>
  <div
    class="border border-gray-200 p-2 rounded-lg flex flex-col w-full max-w-4xl"
  >
    <div class="flex w-full rounded-lg p-2 gap-2">
      <button
        @click="editor.chain().focus().toggleBold().run()"
        class="bg-white border border-gray-200 p-2 rounded-md"
        :class="editor?.isActive('bold') && 'bg-gray-200'"
      >
        <img class="w-5 h-5" src="../assets/icons/bold.svg" />
      </button>

      <button
        @click="editor.chain().focus().toggleItalic().run()"
        class="bg-white border border-gray-200 p-2 rounded-md"
        :class="editor?.isActive('italic') && 'bg-gray-200'"
      >
        <img class="w-5 h-5" src="../assets/icons/italic.svg" />
      </button>
    </div>
    <EditorContent class="p-2 bg-white" :editor="editor" />
  </div>
</template>
