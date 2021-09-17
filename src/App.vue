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

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

.ProseMirror * {
  margin: 0;
  margin-bottom: 0.75em;
}

.editor {
  margin: 0;
  border: 1px solid #dfdfdf;
}
</style>
