<template>
  <!-- card column -->
  <div class="col-12 col-md-6 col-lg-4 mb-4">
    <div class="card h-100">
      <img :src="project.image" class="card-img-top" alt="..." />
      <div class="card-body">
        <h5 class="card-title">{{ project.title }}</h5>
        <p class="card-text border-bottom pb-3">
          {{ project.description }}
        </p>
        <a
          :href="project.href ? project.href : '#project'"
          target="_blank"
          rel="noopener noreferrer"
          class="text-decoration-none borte"
          >View {{ project.isDocumentation ? "Documentation" : "Project" }} ➔</a
        >
      </div>
    </div>
  </div>
  <!-- card column end -->
</template>

<script setup>
import { defineProps } from "vue";
defineProps({
  project: Object,
});
</script>
