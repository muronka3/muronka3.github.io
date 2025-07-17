<template>
  <section id="portfolio" class="portfolio-section">
    <div class="portfolio-header">explore my work</div>
    <div class="portfolio-table">
      <div class="portfolio-row" v-for="(row, i) in rows" :key="i">
        <div class="portfolio-index">{{ row.index }}</div>
        <div class="portfolio-category">{{ row.category }}</div>
        <div class="portfolio-link" v-for="(link, j) in row.links" :key="j">
          <a :href="link.url" class="portfolio-btn" target="_blank">{{ link.label }}</a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'SectionPortfolio',
  data() {
    return {
      rows: [
        { index: '01', category: 'Education', links: [ { label: 'Go Magic', url: '#' }, { label: 'Sengoku', url: '#' } ] },
        { index: '02', category: 'Medicine', links: [ { label: 'Orthohelper', url: '#' }, { label: 'Capella Clinic', url: '#' } ] },
        { index: '03', category: 'Food & Drink', links: [ { label: 'Chimera Brews', url: '#' }, { label: 'Ciao Napoli', url: '#' } ] },
        { index: '04', category: 'Contest', links: [ { label: 'UNESCO', url: '#' }, { label: 'Everink Tattoo', url: '#' } ] },
      ]
    }
  }
}
</script>

<style scoped>
.portfolio-section {
  min-height: 100vh;
  background: #F4F4F4;
  padding: var(--spacing-lg);
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: flex-start;
}
.portfolio-header {
  font-size: 1.1rem;
  margin-bottom: var(--spacing-md);
  color: var(--color-text);
}
.portfolio-table {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: var(--spacing-md);
}
.portfolio-row {
  display: flex;
  align-items: center;
  gap: 120px;
  border-bottom: 1px solid var(--color-text);
  padding: var(--spacing-sm) 0;
}
.portfolio-index {
  width: 36px;
  text-align: center;
  font-size: 1rem;
}
.portfolio-category {
  width: 312px;
  font-size: 1.5rem;
}
.portfolio-link {
  display: flex;
  align-items: center;
  gap: 20px;
}
.portfolio-btn {
  position: relative;
  font-size: 1rem;
  color: var(--color-text);
  text-decoration: none;
  padding: 10px 24px;
  border-radius: 9999px;
  transition: background 0.2s, color 0.2s;
  z-index: 1;
}
.portfolio-btn:hover::after {
  content: '';
  position: absolute;
  left: 50%;
  top: 50%;
  width: 87px;
  height: 29px;
  background: #6999F2;
  border-radius: 9999px;
  opacity: 0.87;
  mix-blend-mode: darken;
  transform: translate(-50%, -50%);
  z-index: -1;
}
</style> 