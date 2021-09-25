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
  <ul>
    <li>
      That’s a bullet list with one …
    </li>
    <li>
      … or two list items.
    </li>
  </ul>
  <p>
    Isn’t that great? And all of that is editable. But wait, there’s more. Let’s try a code block:
  </p>
  <pre><code class="language-css">body {
  display: none;
}</code></pre>
  <p>
    I know, I know, this is impressive. It’s only the tip of the iceberg though. Give it a try and click a little bit around. Don’t forget to check the other examples too.
  </p>
  <blockquote>
    Wow, that’s amazing. Good work, boy! 👏
    <br />
    — Mom
  </blockquote>
`,
    };
  },
};
</script>
