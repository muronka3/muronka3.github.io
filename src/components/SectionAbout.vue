<template>
  <section id="about" class="about-section">
    <div class="about-characters">
      <AnimatedCharacter v-for="n in 3" :key="n" :type="'idle'" :index="n" />
    </div>
    <div class="about-profile">
      <!-- Здесь будет досье и фото -->
      <slot />
    </div>
  </section>
</template>

<script>
import AnimatedCharacter from './AnimatedCharacter.vue';
export default {
  name: 'SectionAbout',
  components: { AnimatedCharacter },
};
</script>

<style scoped>
.about-section {
  min-height: 100vh;
  background: #F4F4F4;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  padding: var(--spacing-lg);
}
.about-characters {
  position: absolute;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 1;
}
.about-profile {
  position: relative;
  z-index: 2;
  background: #D9D9D9;
  border-radius: 20px;
  box-shadow: 0 4px 32px rgba(49,49,49,0.08);
  padding: var(--spacing-lg);
  min-width: 320px;
  min-height: 400px;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style> 