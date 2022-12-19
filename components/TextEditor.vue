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

    onBeforeUnmount(() => editor.value.destroy());

    return { editor };
  },
};
</script>

<template>
  <div
    class="border border-gray-200 p-2 rounded-lg flex flex-col w-full max-w-4xl m-4"
  >
    <div class="flex w-full justify-between rounded-lg p-2">
      <div class="flex gap-2">
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

        <button
          @click="editor.chain().focus().toggleBulletList().run()"
          class="bg-white border border-gray-200 p-2 rounded-md"
          :class="editor?.isActive('bulletList') && 'bg-gray-200'"
        >
          <img class="w-5 h-5" src="../assets/icons/list.svg" />
        </button>

        <button
          @click="editor.chain().focus().toggleOrderedList().run()"
          class="bg-white border border-gray-200 p-2 rounded-md"
          :class="editor?.isActive('orderedList') && 'bg-gray-200'"
        >
          <img class="w-5 h-5" src="../assets/icons/list.svg" />
        </button>
      </div>
      <div class="flex gap-2">
        <button
          @click="editor.chain().focus().undo().run()"
          class="bg-white border border-gray-200 p-2 rounded-md"
          :disabled="!editor?.can().chain().focus().undo().run()"
        >
          <img class="w-5 h-5" src="../assets/icons/arrow-left.svg" />
        </button>

        <button
          @click="editor.chain().focus().redo().run()"
          class="bg-white border border-gray-200 p-2 rounded-md"
          :disabled="!editor?.can().chain().focus().redo().run()"
        >
          <img class="w-5 h-5" src="../assets/icons/arrow-right.svg" />
        </button>
      </div>
    </div>
    <EditorContent class="p-2 bg-white" :editor="editor" />
  </div>
</template>
