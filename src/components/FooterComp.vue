<script setup>
import GitHubIcon from "./GitHubIcon.vue";
</script>

<template>
  <footer>
    <a
      class="icon"
      href="http://github.com/elbhiuni/fcc-markdown-previewer"
      target="_blank"
      rel="noopener noreferrer"
      ><GitHubIcon
    /></a>
  </footer>
</template>

<style scoped>
footer {
  flex: 1 1 auto;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0.5rem;
}

.icon {
  display: inline-block;
  line-height: 0;
  font-size: 1.8rem;
  transition-property: transform;
  transition-duration: 200ms;
  transition-timing-function: ease-in-out;
}

.icon > svg {
  width: 1em;
  height: auto;
}

.icon:hover {
  transform: translateY(-5px);
}

@media (min-width: 1023px) {
  .icon {
    font-size: 1.5rem;
  }
}
</style>
