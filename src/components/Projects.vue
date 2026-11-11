<template>
  <section class="container-fluid mt-5 py-4 px-5" id="projects">
    <!-- Heading Row -->
    <div class="row mb-4">
      <div class="col-12">
        <h1 class="d-inline-block p-2 fs-4">Projects</h1>
        <p>I like building stuff, here you can check the things I made :)</p>
      </div>
    </div>
    <!-- Projects Row -->
    <div class="row justify-content-center">
      <ProjectCard
        v-for="project in projects"
        :project="project"
        :key="project.id" />
    </div>
  </section>
</template>

<script setup>
import ProjectCard from "./ProjectCard.vue";
import { projects } from "../data/projects";
</script>
