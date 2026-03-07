<script setup>
import { onMounted } from "vue";
import "aos/dist/aos.css";
import AOS from "aos";

onMounted(() => {
  AOS.init();
});
</script>

<template>
  <span style="display: none" />
</template>
