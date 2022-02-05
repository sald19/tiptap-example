<template>
  <div id="app" class="h-screen bg-gray-50">
    <tiptap-editor v-model="content" />
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
    return {
      content: `
        <h2>
          Hi there, test
        </h2>
        <p>
          this is a basic <em>basic</em> example of <strong>tiptap</strong>. Sure, there are all kind of basic text styles you’d probably expect from a text editor. But wait until you see the lists:
        </p>
      `,
    };
  },
};
</script>
