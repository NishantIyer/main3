<template>
  <header class="header">
    <nav class="nav">
      <div class="center">
        <router-link to="/" title="Home" class="nav-link">
            <span class="nav-icon">
              <i class="i-uil:home-alt"></i>
            </span>
        </router-link>
          <router-link to="/about" title="About" class="nav-link">
            <span class="nav-icon">
              <i class="i-cib:about-me"></i>
            </span>
            <span class="nav-text"></span>
          </router-link>
          <router-link to="/posts" title="Blog" class="nav-link">
            <span class="nav-icon">
              <i class="i-streamline:interface-edit-write-2-change-document-edit-modify-paper-pencil-write-writing"></i>
            </span>
            <span class="nav-text"></span>
          </router-link>
          <router-link to="/projects" title="Projects" class="nav-link">
            <span class="nav-icon">
              <i class="i-pepicons-print:code"></i>
            </span>
            <span class="nav-text"></span>
          </router-link>
          <a href="https://github.com/NishantIyer" target="_blank" title="GitHub" class="nav-link">
            <span class="nav-icon">
              <i class="i-uil-github-alt"></i>
            </span>
          </a>
          <router-link to="/pics" title="Pictures" class="nav-link">
            <span class="nav-icon">
              <i class="i-uil:picture"></i>
            </span>
            <span class="nav-text"></span>
          </router-link>
      </div>
    </nav>
  </header>
</template>

<style scoped>
.header {
  position: relative;
}

.nav {
  padding: 1.5rem;
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: transparent;
}

.left {
  display: flex;
  align-items: center;
}

.center {
  display: flex;
  align-items: center;
  flex-grow: 1;
  justify-content: center;
}

.right {
  display: flex;
  align-items: center;
}

.nav-link {
  text-decoration: none;
  color: #fff;
  font-weight: bold;
  font-size: 16px;
  padding: 10px 16px;
  border-radius: 8px;
  transition: background-color 0.2s ease;
}

.nav-link:hover {
  background-color: #333;
}

.nav-link:hover .nav-text {
  color: #fff;
}

.nav-link:last-child {
  margin-right: 0;
}

.nav-icon {
  font-size: 18px;
  margin-right: 8px;
}

.nav-text {
  color: #fff;
  transition: color 0.2s ease;
}

.nav-icon i {
  vertical-align: middle;
}
</style>

<script>
export default {
  // ...other script setup
}
</script>
