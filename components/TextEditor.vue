<script>
import { useEditor, EditorContent } from "@tiptap/vue-3";
import StarterKit from "@tiptap/starter-kit";

export default {
  props: ["state"],
  components: {
    EditorContent,
  },

  setup(props) {
    const editor = useEditor({
      content: props.state.content,
      extensions: [StarterKit],
      onUpdate({ editor }) {
        props.state.onChange(editor.getHTML());
      },
    });

    onBeforeUnmount(() => editor.value.destroy());

    return { editor, props };
  },
};
</script>

<template>
  <div
    class="flex flex-col border border-gray-200 p-2 rounded-lg w-full md:max-w-4xl m-4"
  >
    <div class="flex justify-between w-full rounded-lg p-2">
      <div>
        <button
          @click="editor.chain().focus().toggleBold().run()"
          class="border border-gray-200 bg-white rounded-md p-2 m-1"
          :class="editor?.isActive('bold') && 'bg-gray-200'"
        >
          <img class="h-5 w-5" src="../assets/icons/bold.svg" />
        </button>

        <button
          @click="editor.chain().focus().toggleItalic().run()"
          class="border border-gray-200 bg-white rounded-md p-2 m-1"
          :class="editor?.isActive('italic') && 'bg-gray-200'"
        >
          <img class="h-5 w-5" src="../assets/icons/italic.svg" />
        </button>

        <button
          @click="editor.chain().focus().toggleCode().run()"
          class="border border-gray-200 bg-white rounded-md p-2 m-1"
          :class="editor?.isActive('code') && 'bg-gray-200'"
        >
          <img class="h-5 w-5" src="../assets/icons/code.svg" />
        </button>

        <button
          @click="editor.chain().focus().toggleHeading({ level: 1 }).run()"
          class="bg-white border border-gray-200 p-2 rounded-md m-2"
          :class="editor?.isActive('heading', { level: 1 }) && 'bg-gray-200'"
        >
          <p class="h-5 w-5">H1</p>
        </button>
        <button
          @click="editor.chain().focus().toggleHeading({ level: 2 }).run()"
          class="bg-white border border-gray-200 p-2 rounded-md"
          :class="editor?.isActive('heading', { level: 2 }) && 'bg-gray-200'"
        >
          <p class="h-5 w-5">H2</p>
        </button>
        <button
          @click="editor.chain().focus().toggleHeading({ level: 3 }).run()"
          class="bg-white border border-gray-200 p-2 rounded-md m-2"
          :class="editor?.isActive('heading', { level: 3 }) && 'bg-gray-200'"
        >
          <p class="h-5 w-5">H3</p>
        </button>
        <!-- link -->
        <button
          @click="editor.chain().focus().toggleLink().run()"
          class="border border-gray-200 bg-white rounded-md p-2 m-1"
          :class="editor?.isActive('link') && 'bg-gray-200'"
        >
          <img class="h-5 w-5" src="../assets/icons/link.svg" />
        </button>
        <!-- link -->

        <button
          @click="editor.chain().focus().toggleBulletList().run()"
          class="border border-gray-200 bg-white rounded-md p-2 m-1"
          :class="editor?.isActive('bulletList') && 'bg-gray-200'"
        >
          <img class="h-5 w-5" src="../assets/icons/list.svg" />
        </button>

        <button
          @click="editor.chain().focus().toggleOrderedList().run()"
          class="border border-gray-200 bg-white rounded-md p-2 m-1"
          :class="editor?.isActive('orderedList') && 'bg-gray-200'"
        >
          <img class="h-5 w-5" src="../assets/icons/o-list.svg" />
        </button>
      </div>

      <div class="mt-2 md:flex md:gap-2">
        <button
          @click="editor.chain().focus().undo().run()"
          class="bg-white border border-gray-200 p-2 rounded-md"
          :disabled="!editor?.can().chain().focus().undo().run()"
        >
          <img class="h-5 w-5" src="../assets/icons/arrow-left.svg" />
        </button>

        <button
          @click="editor.chain().focus().redo().run()"
          class="bg-white border border-gray-200 p-2 rounded-md mt-5 md:mt-0"
          :disabled="!editor?.can().chain().focus().redo().run()"
        >
          <img class="h-5 w-5" src="../assets/icons/arrow-right.svg" />
        </button>
      </div>
    </div>
    <EditorContent class="p-2 bg-white" :editor="editor" />
  </div>
</template>
