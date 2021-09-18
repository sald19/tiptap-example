<template>
  <div id="app">
    <tiptap-editor v-model="content" class="editor" />
  </div>
</template>

<script>
import TiptapEditor from "./components/TiptapEditor";

export default {
  name: "App",
  components: {
    TiptapEditor,
  },
  data() {
    return { content: "" };
  },
};
</script>
