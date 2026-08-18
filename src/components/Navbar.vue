<template>
  <nav
    class="navbar fixed top-0 left-0 right-0 z-50 flex justify-between items-center px-6 py-3 md:px-10 transition-all duration-300"
    :class="{ 'navbar-scrolled': isScrolled }"
  >
    <a href="#" class="flex items-center gap-2 group">
      <span class="text-lg font-bold tracking-tight text-white/90 group-hover:text-white transition-colors">
        J<span class="text-accent-cyan">.</span>R
      </span>
    </a>

    <ul class="hidden md:flex items-center gap-1">
      <li v-for="link in navLinks" :key="link.href">
        <a
          :href="link.href"
          class="nav-link px-4 py-2 text-[11px] font-medium tracking-[0.15em] uppercase text-white/40 hover:text-white/80 transition-colors duration-300"
        >
          {{ link.label }}
        </a>
      </li>
    </ul>

    <button
      class="md:hidden flex flex-col gap-1.5 p-2"
      @click="isMobileOpen = !isMobileOpen"
      aria-label="Toggle menu"
    >
      <span
        class="block w-5 h-[1.5px] bg-white/60 transition-all duration-300"
        :class="{ 'rotate-45 translate-y-[4.5px]': isMobileOpen }"
      />
      <span
        class="block w-5 h-[1.5px] bg-white/60 transition-all duration-300"
        :class="{ '-rotate-45 translate-y-[-1.5px]': isMobileOpen }"
      />
    </button>
  </nav>

  <Transition name="mobile-menu">
    <div
      v-if="isMobileOpen"
      class="fixed inset-0 z-40 bg-[#080B12]/95 backdrop-blur-xl flex flex-col items-center justify-center gap-6 md:hidden"
    >
      <a
        v-for="link in navLinks"
        :key="link.href"
        :href="link.href"
        class="text-sm font-medium tracking-[0.2em] uppercase text-white/50 hover:text-white transition-colors"
        @click="isMobileOpen = false"
      >
        {{ link.label }}
      </a>
      <a
        href="#contact"
        class="mt-4 flex items-center gap-2 px-5 py-2.5 rounded-full border border-white/10 text-xs font-medium tracking-[0.15em] uppercasetext-accent-cyan"
        @click="isMobileOpen = false"
      >
        <span class="w-1.5 h-1.5 rounded-full bg-accent-cyan" />
        Contacto
      </a>
    </div>
  </Transition>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from "vue";

const navLinks = [
  { label: "Proyectos", href: "#projects" },
  { label: "Tecnologias", href: "#skills" },
  { label: "Experiencia", href: "#experiences" },
  { label: "Contacto", href: "#contact" },
];

const isScrolled = ref(false);
const isMobileOpen = ref(false);

const handleScroll = () => {
  isScrolled.value = window.scrollY > 20;
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<style scoped>
.navbar {
  background: transparent;
}

.navbar-scrolled {
  background: rgba(8, 11, 18, 0.7);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.04);
}

.nav-link {
  position: relative;
}

.nav-link::after {
  content: "";
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--color-accent-cyan), transparent);
  opacity: 0;
  transition: all 0.3s ease;
}

.nav-link:hover::after {
  width: 60%;
  opacity: 0.5;
}

.mobile-menu-enter-active,
.mobile-menu-leave-active {
  transition: all 0.3s ease;
}

.mobile-menu-enter-from,
.mobile-menu-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>
