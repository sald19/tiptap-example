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
      content: {
        type: "doc",
        content: [
          {
            type: "paragraph",
            content: [
              {
                type: "text",
                text: "Example ",
              },
              {
                type: "text",
                marks: [
                  {
                    type: "bold",
                  },
                ],
                text: "Text",
              },
            ],
          },
        ],
      },
    };
  },
};
</script>
