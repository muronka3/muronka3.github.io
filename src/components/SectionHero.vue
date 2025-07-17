<template>
  <section id="hero" class="hero-section">
    <!-- Animated Paperclip and Character -->
    <div class="hero-visual">
      <AnimatedCharacter type="paperclip" />
    </div>
    <div class="hero-content">
      <h1>Hi, I’m Anna.<br>Graphic Designer based in Bishkek</h1>
      <ul class="hero-info">
        <li><span>skills:</span> Graphic Design, Motion Design, Print Design, UX/UI</li>
        <li><span>time zone:</span> GMT +7</li>
        <li><span>languages:</span> English, Russian, German</li>
      </ul>
    </div>
  </section>
</template>

<script>
import AnimatedCharacter from './AnimatedCharacter.vue';
export default {
  name: 'SectionHero',
  components: { AnimatedCharacter },
};
</script>

<style scoped>
.hero-section {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: var(--spacing-lg);
  position: relative;
}
.hero-visual {
  flex: 1 1 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}
.hero-content {
  flex: 1 1 50%;
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  gap: var(--spacing-md);
}
.hero-content h1 {
  font-size: 2.2rem;
  font-weight: 700;
  margin: 0 0 var(--spacing-md) 0;
  text-align: right;
}
.hero-info {
  list-style: none;
  padding: 0;
  margin: 0;
  text-align: right;
}
.hero-info li {
  font-size: 1.1rem;
  margin-bottom: var(--spacing-sm);
}
.hero-info span {
  font-weight: 700;
  margin-right: 0.5em;
}
</style> 