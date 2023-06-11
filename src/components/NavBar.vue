<template>
  <div class="container">
    <header class="header">
      <nav class="nav">
        <div class="left">
          <router-link to="/" title="Home" class="nav-link">
            <span class="nav-icon">
              <i class="i-uil:home-alt"></i>
            </span>
          </router-link>
        </div>
        <div class="center">
          <router-link to="/posts" title="Blog" class="nav-link">
            <span class="nav-text">Blog</span>
          </router-link>
          <router-link to="/academia" title="Academia" class="nav-link">
            <span class="nav-text">Academia</span>
          </router-link>
          <router-link to="/projects" title="Projects" class="nav-link">
            <span class="nav-text">Projects</span>
          </router-link>
        </div>
        <div class="right">
          <a href="https://github.com/NishantIyer" target="_blank" title="GitHub" class="nav-link">
            <span class="nav-icon">
              <i class="i-uil-github-alt"></i>
            </span>
          </a>
          <a href="https://nishantiyer.netlify.app/pics" target="_blank" title="Pictures" class="nav-link">
            <span class="nav-icon">
              <i class="i-uil:picture"></i>
            </span>
          </a>
        </div>
      </nav>
    </header>
  </div>
</template>

<style scoped>
.container {
  max-width: 100%;
  overflow-x: hidden;
}

.header {
  position: relative;
}

.nav {
  padding: 1rem;
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
  font-size: 14px;
  padding: 8px 12px;
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
  font-size: 16px;
  margin-right: 6px;
}

.nav-text {
  color: #fff;
  transition: color 0.2s ease;
}

.nav-icon i {
  vertical-align: middle;
}

@media (max-width: 480px) {
  .nav {
    flex-wrap: wrap;
    padding: 1rem 0;
  }

  .left,
  .center,
  .right {
    width: 100%;
    display: flex;
    justify-content: center;
    margin-bottom: 1rem;
  }

  .nav-link {
    font-size: 16px;
    padding: 8px 12px;
    margin: 0 8px;
  }
}
</style>

<script>
export default {
  // ...other script setup
}
</script>
