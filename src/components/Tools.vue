<template>
  <section class="container-fluid py-5 px-5" id="tools">
    <!-- Heading Row -->
    <div class="row mb-4">
      <div class="col-12 text-center gap-1">
        <h1 class="d-inline-block p-2 fs-4">Tools & Technologies</h1>
        <h2 class="display-5">Developer Toolkit</h2>
        <p>
          The core technologies, frameworks, and developer tools that I use for
          powering modern web applications.
        </p>
      </div>

      <!-- Tools Grid Row START -->
      <div class="row justify-content-center g-4 text-center">
        <!-- card column start -->
        <ToolCard v-for="tool in tools" :tool="tool" />
        <!-- card column end -->
      </div>
    </div>
  </section>
</template>

<script setup>
import ToolCard from "./ToolCard.vue";
import { tools } from "../data/tools.js";
</script>
