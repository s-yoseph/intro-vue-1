<template>
  <div class="hello-page">
    <h1>Hello World</h1>
    <p>This is a dummy feature to demonstrate the spec-driven development workflow.</p>
  </div>
</template>

<script setup>
useHead({
  title: 'Hello World',
  meta: [
    { name: 'description', content: 'A dummy Hello World page for workflow demonstration.' }
  ]
})
</script>

<style scoped>
.hello-page {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  font-family: sans-serif;
}
</style>
