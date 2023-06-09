<script setup lang="ts">
import { isDark } from '~/logics'
import OhVueIcon from "oh-vue-icons";
</script>

<template>
  <header class="header z-40">
    <RouterLink
      class="w-10 h-10 absolute lg:fixed m-6 select-none outline-none"
      to="/"
      focusable="false"
    >
      <img v-show="isDark" src="/logo-dark.svg?url" alt="logo">
      <img v-show="!isDark" src="/logo.svg?url" alt="logo">
    </RouterLink>
    <nav class="nav">
      <div class="spacer" />
      <div class="right">
        <RouterLink to="/posts" title="Blog">
          <span class="lt-md:hidden">Blog</span>
          📝
        </RouterLink>
        <RouterLink to="/projects" title="Projects">
          <span class="lt-md:hidden">Projects</span>
          🧑‍💻
        </RouterLink>
        <RouterLink to="/pics" title="Pics">
          <span class="lt-md:hidden">Gallery</span>
          🖼️
        </RouterLink>
        <RouterLink to="/academia" title="Academia">
          <span class="lt-md:hidden">Academia</span>
          💡
        </RouterLink>
        
   
        <a href="https://github.com/NishantIyer" target="_blank" title="GitHub" class="lt-md:hidden">
          <div i-uil-github-alt />
        </a>
        
      </div>
    </nav>
  </header>
</template>

<style scoped>
.header h1 {
  margin-bottom: 0;
}

.logo {
  position: absolute;
  top: 1.5rem;
  left: 1.5rem;
}

.nav {
  padding: 2rem;
  width: 100%;
  display: grid;
  grid-template-columns: auto max-content;
  box-sizing: border-box;
}

.nav > * {
  margin: auto;
}

.nav img {
  margin-bottom: 0;
}

.nav a {
  cursor: pointer;
  text-decoration: none;
  color: inherit;
  transition: opacity 0.2s ease;
  opacity: 0.6;
  outline: none;
}

.nav a:hover {
  opacity: 1;
  text-decoration-color: inherit;
}

.nav .right {
  display: grid;
  grid-gap: 1.2rem;
  grid-auto-flow: column;
}

.nav .right > * {
  margin: auto;
}
</style>
