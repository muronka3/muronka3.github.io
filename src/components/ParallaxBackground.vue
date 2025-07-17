<template>
  <div class="parallax-bg">
    <!-- Здесь будут абстрактные круги с CSS-анимацией -->
  </div>
</template>

<script>
export default {
  name: 'ParallaxBackground',
};
</script>

<style scoped>
.parallax-bg {
  position: absolute;
  width: 100vw;
  height: 100vh;
  left: 0;
  top: 0;
  pointer-events: none;
  z-index: 0;
  /* Анимации будут добавлены позже */
}
</style> 