<template>
  <div class="m-2 border border-gray-200 bg-white rounded" v-if="editor">
    <menu-bar :editor="editor" />

    <editor-content :editor="editor" class="h-48 overflow-y-auto" />
  </div>
</template>

<script>
import { Editor, EditorContent } from "@tiptap/vue-2";
import * as Y from "yjs";
import { WebrtcProvider } from "y-webrtc";
import CollaborationCursor from "@tiptap/extension-collaboration-cursor";
import CharacterCount from "@tiptap/extension-character-count";
import Collaboration from "@tiptap/extension-collaboration";
import Highlight from "@tiptap/extension-highlight";
import StarterKit from "@tiptap/starter-kit";
import TaskItem from "@tiptap/extension-task-item";
import TaskList from "@tiptap/extension-task-list";

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
    return { editor: null, provider: null };
  },

  mounted() {
    const ydoc = new Y.Doc();

    this.provider = new WebrtcProvider(
      "tiptap-collaboration-extension-test",
      ydoc
    );

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
        Collaboration.configure({
          document: ydoc,
        }),
        CollaborationCursor.configure({
          provider: this.provider,
          user: {
            name: "@sald19",
            color: "#f783ac",
          },
        }),
        Highlight,
        StarterKit.configure({
          history: false,
        }),
        TaskItem,
        TaskList,
      ],
    });
  },

  beforeUnmount() {
    this.editor.destroy();
    this.provider.destroy();
  },
};
</script>

<style>
.prose {
  @apply min-h-full outline-none p-2;
}

/* Give a remote user a caret */
.prose .collaboration-cursor__caret {
  position: relative;
  margin-left: -1px;
  margin-right: -1px;
  border-left: 1px solid #0d0d0d;
  border-right: 1px solid #0d0d0d;
  word-break: normal;
  pointer-events: none;
}

/* Render the username above the caret */
.prose .collaboration-cursor__label {
  position: absolute;
  top: -1.4em;
  left: -1px;
  font-size: 12px;
  font-style: normal;
  font-weight: 600;
  line-height: normal;
  user-select: none;
  color: #0d0d0d;
  padding: 0.1rem 0.3rem;
  border-radius: 3px 3px 3px 0;
  white-space: nowrap;
}
</style>
