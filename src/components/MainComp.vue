<script setup>
import { reactive, computed } from "vue";
import { marked } from "marked";
import DOMPurify from "isomorphic-dompurify";
import markdownText from "../assets/markdownText";

marked.setOptions({
  breaks: true,
  gfm: true,
});

const markdown = reactive({
  text: markdownText,
});

const cleanText = computed(() => {
  // remove the most common zerowidth characters from the start of the file
  const content = markdown.text.replace(
    // eslint-disable-next-line no-misleading-character-class
    /^[\u200B\u200C\u200D\u200E\u200F\uFEFF]/,
    ""
  );
  const parseText = marked.parse(content);
  return DOMPurify.sanitize(parseText);
});
</script>

<template>
  <main>
    <textarea
      name="editor"
      id="editor"
      class="editor"
      v-model="markdown.text"
    ></textarea>
    <div class="separator"></div>
    <div
      id="preview"
      class="markdown-body"
      type="text"
      v-html="cleanText"
    ></div>
  </main>
</template>

<style scoped>
main {
  flex: 1 1 auto;
  display: flex;
  flex-direction: column;
  overflow: hidden;
}

main > .editor {
  flex: 1 1 50%;
  font-size: 1.2rem;
  overflow-y: scroll;
  padding: 10px;
}

main > .separator {
  flex: 1 1 1%;
  background-color: #16a34a;
}

main > .markdown-body {
  flex: 1 1 50%;
  overflow-y: auto;
  padding: 10px;
}

@media (min-width: 1023px) {
  main {
    display: flex;
    flex-direction: row;
  }
}
</style>
