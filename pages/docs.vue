<template>
  <div class="docs-container">
    <header class="docs-header">
      <h1>Project Documentation</h1>
      <p class="subtitle">Guide to building and contributing to intro-vue-1</p>
    </header>

    <main class="docs-content">
      <section class="docs-section">
        <h2>1. Codebase Structure</h2>
        <p>This project is built with Nuxt 3 and styled using custom scoped CSS. Key folders include:</p>
        <ul>
          <li><strong>pages/</strong>: File-based routing (e.g. <code>/admin/login</code>, <code>/hello</code>).</li>
          <li><strong>plans/</strong>: Spec-driven development plan files.</li>
        </ul>
      </section>

      <section class="docs-section">
        <h2>2. Spec-Driven Workflow</h2>
        <p>Every codebase change must adhere to the Golden Rule outlined in the Project Constitution:</p>
        <blockquote>
          Plan &rarr; Issue &rarr; Branch &rarr; Implement &rarr; Secrets Check &rarr; Save Plan &rarr; Confirm Commit &rarr; Confirm PR
        </blockquote>
      </section>

      <section class="docs-section">
        <h2>3. Local Verification</h2>
        <p>Ensure local server runs correctly before committing. Use <code>npm run dev</code> for testing.</p>
      </section>
    </main>
  </div>
</template>

<script setup>
useHead({
  title: 'Project Documentation',
  meta: [
    { name: 'description', content: 'Contribution guide and codebase overview.' }
  ]
})
</script>

<style scoped>
.docs-container {
  max-width: 800px;
  margin: 0 auto;
  padding: 3rem 1.5rem;
  font-family: system-ui, -apple-system, sans-serif;
  color: #1f2937;
  line-height: 1.6;
}

.docs-header {
  border-bottom: 2px solid #e5e7eb;
  padding-bottom: 1.5rem;
  margin-bottom: 2rem;
}

h1 {
  font-size: 2.25rem;
  margin: 0 0 0.5rem 0;
  color: #111827;
}

.subtitle {
  color: #6b7280;
  font-size: 1.125rem;
  margin: 0;
}

.docs-section {
  margin-bottom: 2.5rem;
}

h2 {
  font-size: 1.5rem;
  color: #111827;
  border-bottom: 1px solid #f3f4f6;
  padding-bottom: 0.5rem;
  margin-top: 0;
}

ul {
  padding-left: 1.5rem;
}

blockquote {
  margin: 1rem 0;
  padding: 0.75rem 1rem;
  background-color: #f3f4f6;
  border-left: 4px solid #3b82f6;
  font-style: italic;
  border-radius: 0 4px 4px 0;
}
</style>
