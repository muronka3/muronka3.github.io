<template>
  <header class="header">
    <nav class="nav">
      <a href="#hero" class="nav-link" @click.prevent="scrollTo('hero')">about</a>
      <a href="#portfolio" class="nav-link" @click.prevent="scrollTo('portfolio')">work</a>
      <a href="#reviews" class="nav-link" @click.prevent="scrollTo('reviews')">contact</a>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'HeaderBlock',
  methods: {
    scrollTo(sectionId) {
      const el = document.getElementById(sectionId);
      if (el) {
        el.scrollIntoView({ behavior: 'smooth', block: 'start' });
      }
    }
  }
};
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  z-index: 100;
  background: transparent;
  display: flex;
  justify-content: flex-end;
  padding: var(--spacing-md) var(--spacing-lg) 0 var(--spacing-lg);
}
.nav {
  display: flex;
  gap: var(--spacing-md);
}
.nav-link {
  color: var(--color-text);
  font-family: 'Sono', monospace, sans-serif;
  font-size: 20px;
  text-decoration: none;
  position: relative;
  transition: color 0.2s;
  cursor: pointer;
}
.nav-link::after {
  content: '';
  position: absolute;
  left: 50%;
  top: 50%;
  width: 0;
  height: 0;
  background: url('@/assets/hoveroreol.png') no-repeat center/contain;
  transform: translate(-50%, -50%);
  z-index: -1;
  opacity: 0;
  margin-top: 10px;
  transition: all 0.2s ease-out;
  pointer-events: none;
}

.nav-link:hover::after {
  width: 240px;
  height: 240px;
  opacity: 1;
}
</style> 