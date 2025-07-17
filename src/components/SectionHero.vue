<template>
  <section id="hero" class="hero-section">
    <!-- Visual Composition -->
    <div class="hero-visual">
      <div class="composition-container">
        <!-- Bottom layer: bg-stepple.png -->
        <img src="@/assets/bg-stepple.png" alt="Background" class="composition-bg" />
        <!-- Top layer: paper-clip.png rotated 30 degrees -->
        <img src="@/assets/paper-clip.png" alt="Paperclip" class="composition-top" />
      </div>
    </div>
    
    <!-- Main Content -->
    <div class="hero-content">
      <!-- Left side -->
      <div class="hero-left">
        <span class="hero-tagline">Visual Solutions<br>that convert</span>
      </div>
      
      <!-- Right side: две колонки -->
      <div class="hero-right">
        <div class="hero-columns">
          <div class="hero-col hero-title-col">
            <div class="hero-title">Graphic<br>Designer.</div>
          </div>
          <div class="hero-col hero-name-col">
            <div class="hero-name">Anna<br>Riazanova</div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'SectionHero',
};
</script>

<style scoped>
.hero-section {
  min-height: 100vh;
  position: relative;
  padding: var(--spacing-lg);
  display: flex;
  flex-direction: column;
}

.hero-visual {
  position: absolute;
  top: 40%;
  right: 15%;
  transform: translateY(-50%);
  z-index: 1;
}

.composition-container {
  position: relative;
  width: 500px;
  height: 500px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.composition-bg {
  position: absolute;
  width: 120%;
  height: 120%;
  object-fit: contain;
  z-index: 1;
}

.composition-top {
  position: absolute;
  width: 100%;
  height: 100%;
  object-fit: contain;
  z-index: 2;
  opacity: 1;
}

.hero-content {
  position: absolute;
  bottom: calc(var(--spacing-lg) / 1.5);
  left: var(--spacing-lg);
  right: var(--spacing-lg);
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  z-index: 2;
}

.hero-left {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
}

.hero-tagline {
  font-size: 1.5rem;
  font-weight: 400;
  margin: 0;
  color: var(--color-text);
  font-family: 'Sono', monospace, sans-serif;
  letter-spacing: 0.04em;
  line-height: 1.2;
  white-space: pre-line;
}

.hero-right {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: flex-end;
}

.hero-columns {
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  gap: 1.25rem;
}

.hero-col {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}

.hero-title-col {
  min-width: 0;
}

.hero-title {
  font-size: 3.2rem;
  font-weight: 400;
  margin: 0;
  color: var(--color-text);
  line-height: 1.1;
  font-family: 'Sono', monospace, sans-serif;
  letter-spacing: 0.04em;
}

.hero-name-col {
  min-width: 0;
  padding-left: 1.5rem;
}

.hero-name {
  font-size: 1.5rem;
  font-weight: 400;
  margin: 0;
  color: var(--color-text);
  font-family: 'Sono', monospace, sans-serif;
  letter-spacing: 0.04em;
  white-space: pre-line;
}

/* Responsive adjustments */
@media (max-width: 900px) {
  .composition-container {
    width: 400px;
    height: 400px;
  }
  
  .composition-bg {
    width: 120%;
    height: 120%;
  }
  
  .hero-columns {
    gap: 1.2rem;
  }
  .hero-title {
    font-size: 2.2rem;
  }
  .hero-name {
    font-size: 1.1rem;
  }
}
@media (max-width: 768px) {
  .composition-container {
    width: 300px;
    height: 300px;
  }
  
  .composition-bg {
    width: 120%;
    height: 120%;
  }
  
  .hero-content {
    flex-direction: column;
    gap: var(--spacing-md);
    align-items: flex-start;
  }
  .hero-right {
    align-items: flex-start;
  }
  .hero-title {
    font-size: 1.6rem;
  }
  .hero-name {
    font-size: 1rem;
  }
  .hero-tagline {
    font-size: 1.2rem;
  }
}
</style> 