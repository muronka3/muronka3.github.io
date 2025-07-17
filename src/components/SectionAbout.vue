<template>
  <section id="about" class="about-section">
    <div class="about-characters">
      <AnimatedCharacter v-for="n in 3" :key="n" :type="'idle'" :index="n" />
    </div>
    <div class="about-content">
      <div class="about-intro">
        <h1>Hi, I'm Anna.<br>Graphic Designer based in Bishkek</h1>
        <ul class="about-info">
          <li><span>skills:</span> Graphic Design, Motion Design, Print Design, UX/UI</li>
          <li><span>time zone:</span> GMT +7</li>
          <li><span>languages:</span> English, Russian, German</li>
        </ul>
      </div>
      <div class="about-profile">
        <!-- Здесь будет досье и фото -->
        <slot />
      </div>
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

.about-content {
  position: relative;
  z-index: 2;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: var(--spacing-lg);
  max-width: 800px;
  width: 100%;
}

.about-intro {
  text-align: center;
  margin-bottom: var(--spacing-lg);
}

.about-intro h1 {
  font-size: 2.2rem;
  font-weight: 700;
  margin: 0 0 var(--spacing-md) 0;
  color: var(--color-text);
}

.about-info {
  list-style: none;
  padding: 0;
  margin: 0;
  text-align: center;
}

.about-info li {
  font-size: 1.1rem;
  margin-bottom: var(--spacing-sm);
  color: var(--color-text);
}

.about-info span {
  font-weight: 700;
  margin-right: 0.5em;
}

.about-profile {
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

/* Responsive adjustments */
@media (max-width: 768px) {
  .about-intro h1 {
    font-size: 1.8rem;
  }
  
  .about-info li {
    font-size: 1rem;
  }
}
</style> 