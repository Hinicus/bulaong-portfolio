<template>
  <div class="col-6 col-md-3 col-lg-2">
    <div class="card-tool">
      <div class="container-tool">
        <span><i :class="tool.icon"></i></span>
      </div>
      <h4>{{ tool.title }}</h4>
      <p>{{ tool.description }}</p>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from "vue";
defineProps({
  tool: Object,
});
</script>
