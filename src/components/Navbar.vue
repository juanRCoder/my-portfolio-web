<template>
  <nav
    class="flex justify-between items-center bg-[#111621]/50 backdrop-blur-lg sticky top-0 text-[#C2C6D6] px-6"
  >
    <ul class="flex justify-center items-center gap-5 font-medium text-xs py-6">
      <a href="#skills" class="tracking-[1.2px]">PROYECTOS</a>
      <a href="#experiences" class="tracking-[1.2px]">TECNOLOGIAS</a>
      <a href="#contact" class="tracking-[1.2px]">CONTACTO</a>
    </ul>
    <div>
      <Share2 class="text-[#C2C6D6] cursor-pointer" />
    </div>
  </nav>
</template>
<script setup lang="ts">
import { Share2 } from "@lucide/vue";
</script>
<style lang="css"></style>
