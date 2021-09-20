<template>
  <div class="m-2 border border-gray-200 rounded" v-if="editor">
    <menu-bar :editor="editor" />

    <editor-content :editor="editor" class="h-48 overflow-y-auto" />
  </div>
</template>

<script>
import { Editor, EditorContent } from "@tiptap/vue-2";
import StarterKit from "@tiptap/starter-kit";

import TaskList from "@tiptap/extension-task-list";
import TaskItem from "@tiptap/extension-task-item";
import Highlight from "@tiptap/extension-highlight";
import CharacterCount from "@tiptap/extension-character-count";

import MenuBar from "./MenuBar.vue";

export default {
  name: "TiptapEditor",

  components: {
    EditorContent,
    MenuBar,
  },

  props: {
    value: {
      type: String,
      default: "",
    },
  },

  data() {
    return { editor: null };
  },

  mounted() {
    this.editor = new Editor({
      content: this.value,
      editorProps: {
        attributes: {
          class:
            "prose prose-sm sm:prose lg:prose-lg xl:prose-2xl m-5 focus:outline-none",
        },
      },
      extensions: [
        CharacterCount.configure({
          limit: 10000,
        }),
        StarterKit,
        Highlight,
        TaskList,
        TaskItem,
      ],
    });
  },

  beforeDestroy() {
    this.editor.destroy();
  },
};
</script>

<style>
.prose {
  @apply min-h-full outline-none p-2;
}
</style>
