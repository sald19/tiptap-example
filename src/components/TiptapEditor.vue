<template>
  <div>
    <editor-content :editor="editor" />
  </div>
</template>

<script>
import { Editor, EditorContent } from "@tiptap/vue-2";
import StarterKit from "@tiptap/starter-kit";

export default {
  name: "TiptapEditor",

  components: {
    EditorContent,
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
      extensions: [StarterKit],
    });
  },

  beforeDestroy() {
    this.editor.destroy();
  },
};
</script>
