<script setup>
import MainComp from "./components/MainComp.vue";
import FooterComp from "./components/FooterComp.vue";
</script>

<template>
  <div class="container">
    <header>
      <h1>Markdown Previewer</h1>
    </header>

    <MainComp />

    <FooterComp />
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  height: 100vh;
}

header {
  flex: 1 1 auto;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1rem;
  text-align: center;
}

header > h1 {
  color: white;
  margin: 0;
}
</style>
